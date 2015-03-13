```
title: Instalando PostgreSQL 9.3 e PostGIS 2.1 no Ubuntu 14.04
layout: post
tags: ['post', 'postgresql','9.3', 'postgis', '2.1', 'ubuntu 14.04']
date: 2015-02-19
```

## Remova instalações do PostGIS
O primeiro passo é remover versões antigas do PostGIS se existir.

    sudo apt-get purge postgis

---

## Configurar repositório
Se a versão do seu Ubuntu não for 14.04 (trusty), altere o valor de **trusty**-pgdg para o codinome da sua versão.
**Exemplo**: Se for Ubuntu 14.10, altere para para **utopic**-pgdg.

    wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
    sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt/ trusty-pgdg main" >> /etc/apt/sources.list.d/postgresql.list'

---

## Instalar PostgreSQL e PostGIS
Execute o comando para atualizar a lista de pacotes e instalar o PostgreSQL e a extensão PostGIS.

    sudo apt-get update && sudo apt-get install postgresql-9.3-postgis-2.1 -f

---

## Ativar a extensão PostGIS
Agora, vamos ver como criar um banco de dados com PostGIS ativo. Temos duas maneiras de fazer isso, em que o primeiro deles é o mais recente e simples.

### 1. Usando a instrução CREATE EXTENSION
Isso é tão simples como executar uma consulta no banco de dados onde você deseja ativar o PostGIS.

    CREATE EXTENSION postgis;
ou

### 2. Criar um banco de dados modelo com PostGIS
Esse é um método antigo e tem o mesmo resultado do anterior. Criar um banco de dados modelo com PostGIS irá tornar mais fácil ativar PostGIS para cada novo banco de dados que criar.

    createdb -E UTF8 template_postgis2.1
    psql -d postgres -c "UPDATE pg_database SET datistemplate='true' WHERE datname='template_postgis2.1'"
    
Agora, temos que executar um script SQL que vem junto do PostGIS no banco de dados modelo:

    psql -d template_postgis2.1 -f /usr/share/postgresql/9.3/extension/postgis--2.1.5.sql
    psql -d template_postgis2.1 -c "GRANT ALL ON geometry_columns TO PUBLIC;"
    psql -d template_postgis2.1 -c "GRANT ALL ON geography_columns TO PUBLIC;"
    psql -d template_postgis2.1 -c "GRANT ALL ON spatial_ref_sys TO PUBLIC;"

---

### Crie um banco de dados de teste
Vamos testar a instalação do PostGIS criando um banco de dados de teste.

    createdb test_db -T template_postgis2.1

---
    
### Testando a instalação
Em test_db você pode executar a seguinte instução para ter certeza que você instalou e configurou o PostGIS corretamente:
	
	psql -d test_db

    test_db=# select postgis_version();

    postgis_version---------------------------------------
    2.1 USE_GEOS=1 USE_PROJ=1 USE_STATS=1
    (1 row)

---
    
### Ativar PostGIS para um banco de dados existente
Se você não quer usar a instrução `CREATE EXTENSION` e quer ativar o PostGIS para um banco de dados existente, isso é bastante simples, você só precisa executar o script postgis--2.1.*.sql no seu banco de dados.

    psql -d test_db -f /usr/share/postgresql/9.3/extension/postgis--2.1.5.sql

---

inspirado em http://technobytz.com/install-postgis-postgresql-9-3-ubuntu.html
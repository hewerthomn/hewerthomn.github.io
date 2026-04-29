---
title: "Laravel Error Tracker"
date: 2026-04-28
description: "Um painel simples para acompanhar erros em projetos Laravel sem depender de serviços pagos em projetos de hobby ou testes de ideias."
categories: ["Development"]
tags: ["laravel", "php", "error-tracking", "monitoramento", "open-source"]
images: ["cover.png"]
cover:
image: "cover.png"
alt: "Dashboard do Laravel Error Tracker exibindo issues, eventos e detalhes de erros"
relative: true
hiddenInList: false
hiddenInSingle: false
draft: false
-----------

Eu sempre gostei de criar projetos pequenos para testar ideias.

Alguns viram experimentos rápidos, outros acabam ficando online por mais tempo do que eu imaginava. E quando você coloca alguma coisa em produção, mesmo que seja um projeto de hobby, uma ideia em teste ou uma ferramenta pessoal, uma hora aparece aquela velha pergunta: **será que está tudo funcionando mesmo?**

O problema é que descobrir isso só quando alguém avisa, ou quando você acessa o sistema dias depois e vê que alguma coisa quebrou, não é exatamente o melhor fluxo.

Foi nessa necessidade que comecei a criar o **Laravel Error Tracker**.

<!--more-->

## Por que eu queria isso

Em projetos profissionais, faz todo sentido usar ferramentas maduras para acompanhar erros, alertas e eventos da aplicação.

Mas em projetos pessoais, experimentos, ferramentas pequenas ou ideias que ainda nem sei se vão continuar existindo, sempre ficava meio estranho ter que configurar mais uma solução paga só para acompanhar se apareceu algum erro depois do deploy.

E como eu tenho esse costume de subir projetos de teste, protótipos e pequenas ferramentas, queria algo mais simples:

* instalar dentro do próprio projeto Laravel;
* gravar os erros no banco da aplicação;
* agrupar erros parecidos;
* conseguir ver rapidamente onde o problema aconteceu;
* ter uma tela para resolver, ignorar ou acompanhar uma issue;
* e, principalmente, não depender de um serviço externo para todo projeto pequeno que eu colocasse no ar.

A ideia não era criar um substituto completo para ferramentas grandes de monitoramento.

Era ter um painel simples, direto e suficiente para o meu uso.

## O que ele faz

O **Laravel Error Tracker** é um package para Laravel que registra exceptions da aplicação e organiza esses erros em um dashboard.

Na prática, ele tenta responder algumas perguntas simples:

* qual erro aconteceu?
* em qual rota ou arquivo?
* quantas vezes aconteceu?
* em qual ambiente?
* quando apareceu pela primeira e última vez?
* o erro voltou depois de resolvido?
* existe algum feedback do usuário sobre aquela falha?

Também adicionei alguns recursos para deixar a análise menos cansativa, como o agrupamento do stack trace. Muitas vezes o erro vem com dezenas de linhas do framework, vendor, middleware e chamadas internas, e o que eu realmente quero ver primeiro é: **qual parte do meu código está envolvida nisso?**

Então o painel tenta destacar os frames do projeto e agrupar as partes que são mais de framework ou vendor.

## Um painel para projetos pequenos também

A parte que mais me interessava era essa sensação de poder adicionar o package em projetos pequenos sem muito peso.

Você instala, roda as migrations, configura o gate de acesso ao dashboard e registra a captura das exceptions no `bootstrap/app.php`.

Depois disso, o projeto passa a ter uma área para acompanhar os erros:

```bash
composer require hewerthomn/laravel-error-tracker
php artisan error-tracker:install
php artisan migrate
php artisan error-tracker:doctor
```

Também criei um comando para gerar dados de demonstração, justamente para testar o visual do dashboard e montar screenshots sem precisar usar erro real de produção:

```bash
php artisan error-tracker:demo --fresh --with-feedback --with-notifications --with-resolved
```

## Algumas funcionalidades

Hoje o package já tem algumas coisas que eu queria desde o início:

* dashboard com issues agrupadas;
* detalhes de eventos;
* busca avançada por status, nível, ambiente, rota, arquivo e outros filtros;
* stack trace inteligente;
* notificações;
* cooldown para evitar spam de alerta;
* feedback opcional do usuário na página de erro;
* resolução manual e automática de issues antigas;
* página de diagnóstico da instalação;
* comando `doctor` para verificar se tabelas, colunas e comandos estão corretos;
* dados demo para testar e gerar prints.

Ainda tem muita coisa que pode evoluir, como marcar releases/deploys, criar breadcrumbs, integração com GitHub Issues e talvez captura de erros do frontend.

Mas o básico que eu queria já começou a tomar forma.

## Inspiração

Uma ferramenta que me deu algumas ideias foi o **Faultline**, um projeto de error tracking self-hosted para aplicações Rails.

Achei interessante a ideia de ter um monitor de erros mais próximo da aplicação, sem necessariamente depender de um SaaS externo para tudo. Algumas ideias, como dashboard limpo, agrupamento de erros e fluxo de resolução, combinavam bastante com o que eu queria fazer no Laravel.

Não é uma cópia direta, até porque o ecossistema e a forma de integrar no Laravel são diferentes. Mas foi uma boa referência para pensar: “isso faria sentido como package Laravel?”.

E fazia.

## O que aprendi criando isso

Criar esse package foi um exercício interessante porque ele toca em várias partes do Laravel ao mesmo tempo:

* exception handling;
* service provider;
* publicação de config e migrations;
* commands Artisan;
* views Blade;
* gates de autorização;
* jobs e notificações;
* testes com package;
* documentação e screenshots.

Além disso, um error tracker precisa tomar cuidado para não virar mais um problema. Se ele falha, ele não deveria quebrar a aplicação principal. Então boa parte da implementação também envolve pensar em fallback, diagnóstico e comandos para ajudar quem estiver instalando.

## Documentação

Também criei uma documentação estática com VitePress para separar melhor as coisas.

O README fica como entrada rápida do projeto, enquanto a documentação completa explica instalação, configuração, dashboard, busca avançada, stack trace, feedback, notificações, auto resolve, comandos e segurança.

* Repositório: [https://github.com/hewerthomn/laravel-error-tracker](https://github.com/hewerthomn/laravel-error-tracker)
* Documentação: [https://hewerthomn.com/laravel-error-tracker/](https://hewerthomn.com/laravel-error-tracker/)

## Conclusão

No fim, esse package nasceu de uma necessidade bem simples: eu queria acompanhar melhor os erros dos meus próprios projetos Laravel, principalmente aqueles que são pequenos, experimentais ou feitos para testar uma ideia.

Nem todo projeto precisa começar com uma solução grande de observabilidade.

Às vezes, o que eu preciso é só de um painel honesto, instalado junto da aplicação, que me diga rapidamente: **algo quebrou aqui, nesse arquivo, nessa rota, nesse ambiente, e começou nesse horário**.

E foi exatamente isso que tentei construir com o **Laravel Error Tracker**.

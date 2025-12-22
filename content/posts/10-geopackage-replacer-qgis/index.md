---
title: "Geopackage Replacer"
date: 2025-08-21
description: "Plugin para atualizar rapidamente um .gpkg (ou .zip) usado no projeto, reduzindo a necessidade de fechar e reabrir o QGIS."
categories: ["Development"]
tags: ["qgis","plugin","geopackage","gpkg","zip"]
cover:
  image: "cover.png"
  alt: "Janela do plugin Geopackage Replacer no QGIS mostrando a pré‑visualização de camadas"
  relative: true
  hiddenInList: false
  hiddenInSingle: false
draft: true
---

> **TL;DR**: Criei um plugin para QGIS que substitui um **GeoPackage (.gpkg)** do projeto por uma **nova versão** (também aceita **.zip** contendo o `.gpkg`). A ideia veio da necessidade de **atualizar periodicamente** arquivos sem ter que **fechar e reabrir** o projeto.

## Motivação
Em um projeto precisei atualizar GeoPackages com frequência. O fluxo padrão pedia fechar o projeto, trocar o arquivo e reabrir. O **Geopackage Replacer** elimina esse atrito: você escolhe o novo arquivo (ou `.zip`) e o plugin cuida da troca.

## Como funciona
- Selecione o **GeoPackage atual** que o projeto está usando.
- Escolha o **novo arquivo** (`.gpkg` ou `.zip` com um `.gpkg` dentro).
- O plugin realiza a **substituição** do arquivo referenciado no projeto, reduzindo a necessidade de reiniciar o QGIS.
- Logs informam o andamento e o resultado da troca.

## Instalação
Você pode instalar pelo **Gerenciador de Plugins do QGIS** (Install from ZIP) com o pacote do repositório, ou clonar o código‑fonte para a pasta de plugins do seu perfil.

- Repositório: https://github.com/hewerthomn/geopackage-replacer-qgis-plugin
- Página do plugin: https://plugins.qgis.org/plugins/geopackage_replacer/

## Passo a passo (uso)
1. Abra o projeto no QGIS.
2. Vá em **Plugins → Geopackage Replacer → Open Geopackage Replacer…**
3. Em **Novo arquivo**, selecione o `.gpkg` (ou o `.zip`).
4. Em **Origem**, escolha o GeoPackage atualmente usado no projeto.
5. Clique em **Replace** e aguarde a confirmação.

## Notas
- Ao fornecer um **.zip**, o plugin utiliza o **primeiro `.gpkg`** encontrado dentro do arquivo.
- Em GeoPackages **grandes**, a leitura pode levar alguns segundos.

## Roadmap / ideias futuras
- Pré‑visualização de camadas e metadados antes da troca.
- Opção de backup automático com timestamp.
- Comando via Processing para automação.

## Links
- Código e issues: https://github.com/hewerthomn/geopackage-replacer-qgis-plugin
- Página no repositório de plugins do QGIS: https://plugins.qgis.org/plugins/geopackage_replacer/

---

## Imagens sugeridas para o post
Este post está no formato **Page Bundle** (pasta com `index.md`). Salve as imagens **na mesma pasta**:

1. **Janela do plugin** (use como `cover.png`).
2. **Antes e depois** no painel de **Camadas**.
3. Pasta de backups (se habilitar no futuro), mostrando arquivos com timestamps.
4. **Gerenciador de Plugins** do QGIS com o plugin selecionado.

Para inserir as imagens, use:

```md
![Pré‑visualização do plugin](screenshot-preview.png)
![Exemplo de troca](screenshot-replace.png)
---
title: Eolis
slug: eolis
date: 2025-03-15
draft: true
images: ["images/eolis.jpg"]
thumbnail: "images/thumbnail/eolis.jpg"
categories: ['Development']
tags: ['laravel']
---

## Sistema Unificado da Corregedoria-Geral de Rondônia e seu Impacto na Eficiência do TJRO

O Sistema Eolis é a plataforma unificada da Corregedoria-Geral de Justiça do Estado de Rondônia, criada para otimizar gestão, transparência e decisões baseadas em dados no TJRO. Sua implementação reflete o compromisso com a modernização e o aprimoramento judicial, sendo fundamental para alcançar as metas do CNJ e o Prêmio CNJ de Qualidade. O Eolis abrange diversos módulos para administração e monitoramento, consolidando-se como essencial para a eficiência do judiciário rondoniense. A existência deste sistema unificado demonstra uma abordagem estratégica e inovadora, utilizando a tecnologia para melhoria contínua e integrando diferentes áreas para um ambiente judicial mais coeso e eficiente 1.

## A Gênese do Eolis: Um Projeto Nascido no Recesso Forense de 2017
A idealização do Eolis ocorreu no recesso forense de 2017, quando Everton Inocencio, Maicon Cucchi e Jacob Nery iniciaram o projeto. A escolha desse período demonstra a dedicação da equipe fundadora e a percepção da urgência em criar o sistema. Essa iniciativa revela um comprometimento pessoal e a identificação de uma oportunidade significativa de melhoria nos processos da Corregedoria-Geral. É provável que a equipe inicial tenha identificado lacunas nos processos existentes e visualizado o potencial da tecnologia para otimizar as operações do TJRO. Segundo Jacob Rodrigues Nery, a motivação inicial era automatizar rotinas e permitir a extração independente de dados pelos usuários 4.

## Um Esforço Colaborativo: As Pessoas por Trás do Desenvolvimento do Eolis
O desenvolvimento do Eolis foi marcado pela colaboração de diversas pessoas ao longo dos anos, enriquecendo a funcionalidade do sistema para atender às necessidades do TJRO. Essa participação diversificada contribuiu para a aceitação e integração do sistema nas rotinas do tribunal, garantindo que atendesse às necessidades específicas de cada área. Além da equipe inicial, outros servidores como Renan Barbosa e Ricardo Machado, bem como estagiários, também contribuíram para o desenvolvimento do Eolis durante o biênio 2016/2017 4. Esse esforço de equipe multidisciplinar foi crucial para o sucesso do projeto, combinando diferentes habilidades e perspectivas.

## Do Mito à Realidade: A Nomenclatura do Eolis
O nome "Eolis" deriva da figura mitológica grega de Eolo, deus dos ventos. Inicialmente chamado de "Eoles", o nome foi adaptado para "Eolis" para maior clareza, refletindo uma preocupação com a usabilidade. A conexão com os ventos remete ao projeto de ETL "Ventos", responsável pelo fluxo de dados no sistema, sugerindo uma visão integrada onde os dados são essenciais para o judiciário. A priorização da clareza na nomenclatura demonstra atenção à experiência do usuário e à compreensão do sistema pela comunidade do TJRO, utilizando uma metáfora para representar o tratamento dos dados.

## A Evolução da Integração de Dados: Ventos e sua Transição para o Apache Airflow
O projeto "Ventos" é responsável pelo ETL no Eolis. Inicialmente implementado com o Oracle Data Integrator (ODI), no final de 2020 iniciou-se a migração para o Apache Airflow, uma plataforma de código aberto para orquestração de fluxos de trabalho de dados. Essa mudança estratégica visou maior flexibilidade, redução de custos, escalabilidade, acesso a uma comunidade ativa e aproveitamento de funcionalidades avançadas 5. O Apache Airflow oferece flexibilidade e uma vasta gama de conectores, sendo adequado para orquestrar processos de ETL 5. A transição para o Apache Airflow indica uma decisão estratégica do TJRO em direção a maior autonomia tecnológica e soluções mais adaptáveis para a gestão de dados judiciais.

## Entendendo o Eolis: Um Sistema OLAP Híbrido
O Eolis é um sistema OLAP híbrido, combinando diferentes arquiteturas como MOLAP, ROLAP e possivelmente HOLAP, para otimizar o desempenho e o acesso aos dados para diversas análises 8. Essa abordagem permite análises detalhadas e uma visão multidimensional do desempenho judicial, atendendo a diversas necessidades analíticas, desde relatórios específicos até a identificação de tendências. Uma arquitetura OLAP híbrida oferece o equilíbrio entre a velocidade de análise de dados pré-calculados e a flexibilidade de consultar dados diretamente do banco de dados relacional 8, tornando o Eolis uma ferramenta poderosa para monitoramento e tomada de decisões estratégicas.

## Um Mergulho na Funcionalidade do Eolis: Módulos que Fortalecem o TJRO
O Eolis possui diversos módulos com funcionalidades específicas:
Módulo de Monitoramento (Processos Paralisados): Acompanha processos paralisados, permitindo intervenção para melhorar a eficiência processual e reduzir o acúmulo de processos 11. Segundo o juiz Rinaldo Forti, o sistema foi fundamental para a gestão das unidades judiciais 4, contribuindo para a Meta 1 do CNJ 14.
Módulo de Autocorreição: Suporta a autoavaliação e a melhoria contínua, promovendo transparência e responsabilidade 16. A Corregedoria de Justiça de Minas Gerais também utiliza um sistema de autocorreição 16.
Módulo de Promoção de Magistrado (Geração do Relatório de Promoção): Automatiza a geração de relatórios para promoções, garantindo objetividade e transparência 17, alinhado com as diretrizes do CNJ 19.
Módulo Presente (Frequência de Pessoas em Cumprimento de Medida ou Pena Alternativa): Acompanha a frequência e o cumprimento de medidas alternativas 20, essencial para a gestão eficaz dessas sanções.
Módulo NUPS (Núcleo Psicossocial) com Integração do SEEU e PJE: Integra informações psicossociais com dados processuais e de execução penal do SEEU e PJE 23, demonstrando uma abordagem holística do sistema judicial. O SEEU é um sistema do CNJ para unificar a gestão da execução penal 24.
Módulo PRECALC (Cálculo da Prescrição): Automatiza o cálculo dos prazos prescricionais, garantindo segurança jurídica e evitando erros processuais 25.
Módulo Argus (Acompanhamento das Metas do CNJ e Prêmio CNJ de Qualidade): Monitora o progresso em relação às metas do CNJ e aos critérios do Prêmio CNJ de Qualidade 28, auxiliando o TJRO a avaliar seu desempenho.

## Fundamentos Técnicos: A Arquitetura e Tecnologias do Eolis
A arquitetura do Eolis utiliza tecnologias modernas:
Camada de Aplicação: Laravel Framework: Desenvolvido com Laravel, um framework PHP robusto que facilita o desenvolvimento eficiente e a manutenibilidade do sistema 30, utilizando a arquitetura MVC e oferecendo funcionalidades de segurança.
Camada de Banco de Dados: PostgreSQL e Datamart em Oracle: Utiliza PostgreSQL para a aplicação desde 2022, após migração do Oracle 32. Possui um datamart em Oracle 34 para relatórios analíticos, aproveitando a expertise e funcionalidades específicas dessa tecnologia para análise de grandes volumes de dados.

## O Impacto do Eolis no Desempenho do TJRO e no Reconhecimento do CNJ
Desde sua implementação, o Eolis tem auxiliado o TJRO a alcançar as metas do CNJ e a obter o Prêmio CNJ de Qualidade 4. O monitoramento de processos paralisados contribui para a eficiência processual 14, e o módulo Argus acompanha o progresso em relação às metas. A automatização de relatórios de promoção promove a transparência. O ministro Humberto Martins elogiou o sistema de monitoramento 36, e o Prêmio CNJ de Qualidade reconhece os tribunais que se destacam na gestão 28.

## Eolis como Pedra Angular da Eficiência e Excelência no TJRO
Em conclusão, o Eolis é uma plataforma unificada e tecnologicamente avançada que suporta diversas funções cruciais no TJRO. Desde sua concepção em 2017 até sua evolução contínua, o sistema se tornou indispensável para aprimorar a eficiência, a transparência e a tomada de decisões baseada em dados. Sua arquitetura híbrida OLAP, a migração para o Apache Airflow e o uso de tecnologias modernas demonstram um compromisso com a inovação. Os diversos módulos atendem a uma vasta gama de necessidades da administração judicial. A contribuição do Eolis para o alcance das metas do CNJ e para a obtenção do Prêmio CNJ de Qualidade reforça sua importância estratégica para o TJRO, sendo um exemplo de como a tecnologia pode transformar o setor público. A trajetória do Eolis demonstra que iniciativa e colaboração podem levar a melhorias significativas no judiciário, servindo de modelo para outros tribunais.

Referências citadas
1. Entenda porque a informação é o ativo mais importante de uma organização - Servidor - Poder Judiciário de Santa Catarina, acessado em março 16, 2025, https://www.tjsc.jus.br/web/servidor/dicas-de-ti/-/asset_publisher/0rjJEBzj2Oes/content/entenda-porque-a-informacao-e-o-ativo-mais-importante-de-uma-organizacao
2. Artigo aborda a gestão de dados no fortalecimento do CNJ, acessado em março 16, 2025, https://www.cnj.jus.br/artigo-aborda-a-gestao-de-dados-no-fortalecimento-do-cnj/
3. Análise de Dados no Judiciário: benefícios e exemplos - Tríades, acessado em março 16, 2025, https://triades.vc/blog/analise-dados-judiciario-beneficios-exemplos
4. Ventos e Eolis: Corregedoria lança novas ferramentas que integram dados e melhoram o monitoramento de metas | Tudo Rondônia, acessado em março 16, 2025, https://www.tudorondonia.com/noticias/ventos-e-eolis-corregedoria-lanca-novas-ferramentas-que-integram-dados-e-melhoram-o-monitoramento-de-metas-,4817.shtml
5. Apache Airflow vs Oracle BPM comparison - PeerSpot, acessado em março 16, 2025, https://www.peerspot.com/products/comparisons/apache-airflow_vs_oracle-bpm
6. Apache Airflow vs Oracle Data Integrator (ODI) - TrustRadius, acessado em março 16, 2025, https://www.trustradius.com/compare-products/apache-airflow-vs-oracle-data-integrator
7. Compare Airflow versus Oracle Data Integrator (ODI) - there's a better alternative for ETL!, acessado em março 16, 2025, https://kondado.io/en/comp/airflow-versus-oracle-data-integrator-(odi).html
8. O que é OLAP? – Explicação sobre processamento analítico online - AWS, acessado em março 16, 2025, https://aws.amazon.com/pt/what-is/olap/
9. Databases, Data Warehouses, and OLAP | Request PDF - ResearchGate, acessado em março 16, 2025, https://www.researchgate.net/publication/251129610_Databases_Data_Warehouses_and_OLAP
10. SIRO - Sistema de Informação de Risco Operacional - Management Solutions, acessado em março 16, 2025, https://www.managementsolutions.com/sites/default/files/publicaciones/pt/siro.pdf
11. Cursos Abertos - Portal CNJ, acessado em março 16, 2025, https://www.cnj.jus.br/centro-de-formacao-e-aperfeicoamento-de-servidores-do-poder-judiciario/cursos-abertos/
12. Estudo Técnico Preliminar - Lei 14.133/2021 - novo quantitativo (0719341) SEI 003636/2024 / pg. 1 - TCE-RO, acessado em março 16, 2025, https://tce.ro.gov.br/Licitacao/arquivos/Arquivos/Arquivo_INEXI_162024_07-08-24110818Estud.pdf
13. PRORROGAÇÃO DAS INSCRIÇÕES A Comissão Organizadora do Concurso Público de Servidores do PJRO, no uso de sua, acessado em março 16, 2025, https://arquivos.qconcursos.com/regulamento/arquivo/80324/tj_ro_2024_edital_n_1-edital.pdf
14. CNJ: Tribunais buscam melhores índices de eficiência da Justiça em metas para 2025, acessado em março 16, 2025, https://www.trf2.jus.br/jf2/noticia-jf2/2025/cnj-tribunais-buscam-melhores-indices-de-eficiencia-da-justica-em-metas-para
15. Meta Nacional 1: Justiça já julgou mais de 25,3 milhões de processos até outubro de 2024 - TRT/RJ, acessado em março 16, 2025, https://trt1.jus.br/web/guest/ultimas-noticias/-/asset_publisher/IpQvDk7pXBme/content/meta-nacional-1-justica-ja-julgou-mais-de-25-3-milhoes-de-processos-ate-outubro-de-2024/21078?_com_liferay_asset_publisher_web_portlet_AssetPublisherPortlet_INSTANCE_IpQvDk7pXBme_assetEntryId=31084810
16. Notícias, acessado em março 16, 2025, https://ccoge.org.br/noticias?start=378
17. Inscrições - I Congresso de Inovação em Inteligência Artificial no Judiciário - TJPR, acessado em março 16, 2025, https://www.tjpr.jus.br/web/congressoia/inscricoes
18. Concurso TJ RO - Tribunal de Justiça do Estado de Rondônia - Gran Cursos Online, acessado em março 16, 2025, https://www.grancursosonline.com.br/concurso/tj-ro-tribunal-de-justica-do-estado-de-rondonia
19. Texto compilado a partir da redação dada pela Resolução n. 426/2021 e pela Resolução n. 507/2023. RESOLUÇÃO No 106, DE 6, acessado em março 16, 2025, https://atos.cnj.jus.br/files/compilado141736202306146489cc00f1865.pdf
20. FUNDAMENTOS SOBRE ARMAS DE FUEGO Y MUNICIONES - United Nations Office on Drugs and Crime, acessado em março 16, 2025, https://www.unodc.org/documents/e4j/Firearms/E4J_Firearms_Module_02_-_Basics_on_Firearms_and_Ammunition_ES_final.pdf
21. operación y mantenimiento de calderas de vapor pirotubulares en establecimientos de salud - FI-Admin, acessado em março 16, 2025, https://fi-admin.bvsalud.org/document/view/m9nch
22. Módulo de Usuarios Comerciales – MUCOM - Argentina.gob.ar, acessado em março 16, 2025, https://www.argentina.gob.ar/sites/default/files/modulo_de_usuarios_comerciales_-_mucom.pdf
23. Processo Judicial Eletrônico - PJe — Tribunal de Justiça do Distrito Federal e dos Territórios - TJDFT, acessado em março 16, 2025, https://www.tjdft.jus.br/pje
24. Sistema Eletrônico de Execução Unificado (SEEU) - CNJ, acessado em março 16, 2025, https://www.cnj.jus.br/wp-content/uploads/2020/10/Folder-SEEU.pdf
25. Pre-Calculus GT - Curriculum - HCPSS, acessado em março 16, 2025, https://www.hcpss.org/f/academics/math/pre-calc-gt-curriculum.pdf
26. Mixed Review Operations on functions precalc 1.5c larson precalculus how - YouTube, acessado em março 16, 2025, https://www.youtube.com/watch?v=HsAn6E8JRNk
27. PreCalc Functions Intro Pt 4 Q08 | New Jersey Center for Teaching and Learning, acessado em março 16, 2025, https://njctl.org/video/?v=3NlQJ_mr0Xw
28. Prêmio CNJ de Qualidade - Portal CNJ, acessado em março 16, 2025, https://www.cnj.jus.br/pesquisas-judiciarias/premio-cnj-de-qualidade/
29. Resultados - Portal CNJ, acessado em março 16, 2025, https://www.cnj.jus.br/pesquisas-judiciarias/premio-cnj-de-qualidade/resultados-premiocnj/
30. Laravel vs Node: Uma Comparação Detalhada - Kinsta®, acessado em março 16, 2025, https://kinsta.com/pt/blog/laravel-vs-node/
31. PHP - Laravel, Symfony e Zend - Blog Gran Cursos Online, acessado em março 16, 2025, https://blog.grancursosonline.com.br/php-laravel-symfony-e-zend/
32. PostgreSQL: banco de dados escalável e seguro - Arsys, acessado em março 16, 2025, https://www.arsys.pt/cloud/dbaas/postgresql
33. PostgreSQL: Impulsionando Softwares com Segurança e História - Acsiv Sistemas, acessado em março 16, 2025, https://acsiv.com.br/blog/2023/08/15/postgresql-impulsionando-softwares-com-seguranca-e-historia/
34. Edital 01-2024 - Versão final 03-12-2024 - Documentos Google - TRT15, acessado em março 16, 2025, https://trt15.jus.br/sites/portal/files/transparencia/concursos/servidores/Concurso%202024-2025/Edital%2001-2024%20-%20Vers%C3%A3o%20final.pdf
35. Datamart-OBIEE-Overview.pdf - Oregon.gov, acessado em março 16, 2025, https://www.oregon.gov/das/Financial/AcctgSys/Documents/Datamart-OBIEE-Overview.pdf
36. Corregedor conhece sistema de monitoramento da corregedoria de Rondônia - Portal CNJ, acessado em março 16, 2025, https://www.cnj.jus.br/corregedor-conhece-sistema-de-monitoramento-da-corregedoria-de-rondonia/
37. EXCELÊNCIA - TJRR conquista o mais alto reconhecimento no Prêmio CNJ de Qualidade, acessado em março 16, 2025, https://www.tjrr.jus.br/index.php/noticias/18819-excelencia-tjrr-conquista-o-mais-alto-reconhecimento-no-premio-cnj-de-qualidade

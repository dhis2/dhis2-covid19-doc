# Notas de Lançamento do Pacote COVID-19 v0.3

## Resumo

Fizemos várias actualizações ao pacote existente para o alinhar com o novo COVID-19 [directrizes de vigilância divulgadas pela OMS em 20 de Março de 2020](https://www.who.int/emergencies/diseases/novel-coronavirus-2019/technical-guidance/surveillance-and-case-definitions) e introduzimos novos componentes no pacote global de apoio. Por favor, reveja as notas aqui e contacte-nos no fórum de discussão da COVID-19 na [comunidade de práticas](https://community.dhis2.org/c/implementation/covid-19/) com quaisquer questões.

**Todos os pacotes de metadados e documentação podem ser descarregados de [dhis2.org.covid-19](https://www.dhis2.org/pt/covid-19).**

Os pacotes estão actualmente traduzidos para francês, espanhol, português e russo, com línguas adicionais no pipeline (árabe, lao, birmanês). Podemos suportar traduções de pacotes de metadados na nossa plataforma global de tradução e convidamos a comunidade a contribuir se o seu país estiver interessado em traduzir o pacote para uma nova língua. [Veja o anúncio da nossa Comunidade de Práticas ](https://community.dhis2.org/t/the-new-dhis2-translation-platform-is-now-available/37755)e comece a contribuir como tradutor aqui [juntando-se à plataforma de tradução DHIS2](https://docs.dhis2.org/master/en/implementer/html/user-interface-localization.html#translation-server). Por favor contacte-nos em translate@dhis2.org.

O novo lançamento inclui:

1. Programa de rastreio de vigilância com base em casos COVID-19 (v0.3.3)
2. Programa de Registro e Acompanhamento de Contatos COVID-19 (v0.3.2)
3. Programa de Eventos de Vigilância COVID-19 (v0.3.2)
4. Relatório de vigilância agregada COVID-19 (v0.3.2)
5. **NOVO** Programa de rastreio dos pontos de entrada (v0.3.1)

## Programa de Vigilância com Base em Casos COVID-19 (Tracker)

1. Códigos de metadados actualizados para se alinharem com o [dicionário de dados da OMS baseado em casos de notificação](https://www.who.int/docs/default-source/coronaviruse/2020-02-27-data-dictionary-en.xlsx)
2. Indicadores do programa actualizados para reflectir as novas definições de casos prováveis da OMS (consultar as definições de casos actualizadas nas orientações de vigilância provisórias actualizadas de 20 de Março de 2020 [orientações de vigilância provisórias da OMS actualizadas de 20 de Março de 2020](https://apps.who.int/iris/bitstream/handle/10665/331506/WHO-2019-nCoV-SurveillanceGuidance-2020.6-eng.pdf))
3. As lendas etárias foram actualizadas para satisfazer as novas orientações da OMS para a comunicação semanal
4. relationshipType adicionado ao pacote de metadados
5. Pequenas correcções aos metadados para permitir uma instalação mais fácil do pacote (ou seja, indicadorType UID corresponde ao tipo de indicador incluído no pacote agregado)

## Programa de Registo e Acompanhamento de Contactos COVID-19 (Tracker)

1. Foi acrescentada uma nova fase ao programa para permitir o "acompanhamento" repetido de um contacto de caso. Esta fase foi acrescentada para reflectir os fluxos de trabalho implementados no Uganda e no Togo, onde os contactos podem ser repetidamente monitorizados ao longo de 14 dias para determinar se existem sintomas. O ***programa*** baseia-se nas directrizes da OMS que podem ser encontradas [aqui](https://www.who.int/internal-publications-detail/considerations-in-the-investigation-of-cases-and-clusters-of-covid-19), bem como nas informações obtidas através do sítio Web [OpenWHO](https://openwho.org/courses/introduction-to-ncov).
2. As lendas etárias foram actualizadas para satisfazer as novas orientações da OMS para a comunicação semanal
3. relationshipType adicionado ao pacote de metadados
4. Pequenas correcções aos metadados para permitir uma instalação mais fácil do pacote

### Programa de Notificação de Eventos COVID-19

1. Regras do programa actualizadas para evitar erros na apresentação do formulário na visualização em linha (ver [Jira issue 8519](https://jira.dhis2.org/browse/DHIS2-8519))
2. Indicadores do programa actualizados para reflectir as novas definições de casos da OMS
3. As lendas etárias foram actualizadas para satisfazer as novas orientações da OMS para a comunicação semanal
4. Pequenas correcções aos metadados para permitir uma instalação mais fácil do pacote

### Relatórios de Vigilância Agregados COVID-19 

As seguintes actualizações foram feitas para reflectir as novas orientações [directrizes da OMS actualizadas em 20 de Março de 2020](https://apps.who.int/iris/bitstream/handle/10665/331506/WHO-2019-nCoV-SurveillanceGuidance-2020.6-eng.pdf), incluindo a actualização da informação global agregada à OMS (semanal e diária)

1. Categorias etárias actualizadas de acordo com novas faixas etárias
2. Novos indicadores adicionados para a proporção de homens entre os casos confirmados e para a proporção de homens entre as mortes confirmadas
3. Novo conjunto de dados semanais para a classificação da transmissão a nível subnacional um (ou seja, provincial - pode ser atribuído a qualquer nível subnacional, conforme adequado no país) por orientações actualizadas da OMS em matéria de transmissão semanal
4. Pequenas correcções aos metadados para permitir uma instalação mais fácil do pacote

### **NOVO** Programa de rastreio de pontos de entrada

O caso de utilização do programa "Points of Entry tracker" foi concebido para apoiar o registo de viajantes que entram num país com um historial de viagem ou residência num país/área/território que comunique a transmissão local da COVID-19 e que possam ter de ser acompanhados para garantir que não se desenvolvem sintomas. Baseia-se na concepção implementada pela HISP Sri Lanka para apoiar o Ministério da Saúde do Sri Lanka com pequenas alterações para tornar o programa mais genérico para uso global e para se alinhar com os outros programas de rastreio do pacote COVID-19. O pacote apoia intervenções nos pontos de entrada detalhados na OMS [orientação técnica para a gestão de pessoas doentes nos pontos de entrada] (https://www.who.int/emergencies/diseases/novel-coronavirus-2019/technical-guidance/points-of-entry-and-mass-gatherings).

Por favor leia mais sobre o programa POE no [documento de concepção do sistema](https://docs.google.com/document/d/1PJ4iRJGmUBv6jF7hcACxt-dhd5JRpeBt0mKxgPBsmvc/edit#).

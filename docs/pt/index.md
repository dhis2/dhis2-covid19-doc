# Pacote de Dados Digitais de Vigilância COVID-19

O DHIS2 lançou um pacote de dados digitais para acelerar a detecção de casos, a comunicação de situações, a vigilância activa e a resposta ao COVID-19. O pacote é inspirado na concepção pioneira do rastreador DHIS2 do Ministério da Saúde do Sri Lanka para a detecção de casos do COVID-19 e baseia-se em anos de colaboração com a Organização Mundial de Saúde (OMS) para desenvolver normas de sistemas de informação para a vigilância de doenças com base em casos. O pacote de dados digitais COVID-19 inclui metadados normalizados alinhados com as [orientações técnicas sobre vigilância COVID-19 e definições de casos] da OMS (https://www.who.int/emergencies/diseases/novel-coronavirus-2019/technical-guidance/surveillance-and-case-definitions) e orientações de implementação para permitir uma implantação rápida nos países.

O DHIS2 está actualmente a ser utilizado para a vigilância COVID-19 em países de todo o mundo. Explore o mapa abaixo para ver onde os pacotes DHIS2 COVID-19 estão a ser testados e implantados.


## Para que pode ser utilizado o Pacote de Vigilância DHIS2 COVID-19?

O pacote suporta fluxos de trabalho de vigilância e análise automatizada para componentes-chave da vigilância de rotina e activa:

*   **COVID-19 Vigilância baseada em casos [tracker]**: regista e rastreia casos suspeitos; capta sintomas, demografia, factores de risco e exposições; cria pedidos de laboratório; liga casos confirmados a contactos; e monitoriza os resultados dos pacientes. Este pacote pode ser instalado como um pacote autónomo COVID-19 ou pode ser integrado no rastreador integrado de vigilância e resposta a doenças existente num país.
*   **Programa de registo e acompanhamento de contactos [localizador]**: reforça a detecção activa de casos através de actividades de localização de contactos, tais como a identificação e acompanhamento de contactos de um caso suspeito ou confirmado de COVID-19.
*   **Programa de rastreio e acompanhamento dos portos de entrada [tracker]**: inscreve os viajantes que visitaram locais de alto risco nos portos de entrada para um acompanhamento e acompanhamento de 14 dias.
*   **COVID-19 Programa de Eventos de Vigilância [evento]**: uma lista de linhas simplificada que capta um subconjunto de pontos mínimos de dados críticos para facilitar uma análise e resposta rápidas, particularmente útil quando a carga de casos ou a carga de comunicação excede a capacidade do localizador de vigilância baseado em casos
*   **COVID-19 Vigilância agregada [agregada]**: um conjunto de dados agregado que captura o mínimo de pontos de dados necessários para a comunicação diária ou semanal

Todos os pacotes de dados digitais estão optimizados para a recolha de dados do Android com a DHIS2 Capture App, que pode ser descarregada gratuitamente na loja [Google Play](https://play.google.com/store/apps/details?id=com.dhis2&hl=en).

Trabalha num país interessado em instalar o rastreador DHIS2 COVID-19? Por favor contacte-nos em [post@dhis2.org](mailto:post@dhis2.org).


## Teste a demonstração de vigilância do DHIS2 COVID-19

Explore o DHIS2 COVID-19 Surveillance Tracker por si próprio utilizando a nossa base de dados de demonstração online (login obrigatório): **[DHIS2 COVID-19 Surveillance Interactive Demo](https://covid.dhis2.org/demo)**

## Descarregar o pacote de vigilância DHIS2 COVID-192 COVID-19 Surveillance Package

As seguintes versões do pacote de vigilância DHIS2 COVID-19 estão disponíveis para download e instalação. O pacote de configuração do COVID-19 consiste em metadados DHIS2 que fornecem uma configuração padrão do DHIS2 de acordo com [as últimas recomendações da OMS disponíveis](https://www.who.int/emergencies/diseases/novel-coronavirus-2019/technical-guidance/surveillance-and-case-definitions)

Ver [v 0.3 notas de lançamento do pacote](release-notes-v03.md) para um resumo das actualizações e dos novos componentes.

Por favor, consulte os seguintes documentos específicos do pacote antes de começar:

*   O **Documento de Concepção do Sistema** fornece detalhes sobre o caso de utilização e configuração do pacote.
*   O **Guia de Instalação** fornece orientações sobre a preparação, importação e adaptação do pacote.

Estão também disponíveis os seguintes recursos em linha:

*   O **[Guia de Implementação do Rastreador](https://docs.dhis2.org/master/en/dhis2_tracker_implementation_guide/target-audience.html)** fornece orientações gerais sobre o planeamento de uma instância de Rastreador DHIS2.
*   O documento **[Perguntas Mais Frequentes](https://community.dhis2.org/t/frequently-asked-questions-faq/38690)** fornece respostas a perguntas comuns sobre o pacote.
*   O **[Canal de Discussão e Apoio COVID-19](https://community.dhis2.org/c/implementation/covid-19/41)** sobre a Comunidade de Prática DHIS2 é um fórum onde pode fazer perguntas, obter apoio para a sua implementação e rever questões que foram levantadas e resolvidas por outros membros da comunidade.

<table style="margin-bottom:1em;">
  <tr>
   <td>
<strong>Versão do DHIS2</strong>
   </td>
   <td><strong>Versão do Pacote</strong>
   </td>
   <td><strong>Tipo de Pacote</strong>
   </td>
   <td><strong>Documentação</strong>
   </td>
   <td><strong>Metadados</strong>
   </td>
   <td><strong>Última Actualização</strong>
   </td>
  </tr>
  <tr>
   <td>2.33
   </td>
   <td>V 0.3.3
   </td>
   <td>Rastreador de vigilância com base em casos do COVID-19 
<p>
Contacto de Registo e Seguimento do COVID-19
   </td>
   <td><a href="https://docs.google.com/document/d/12-pex7VOMoRAnsiIcTLq0mTD6UTSfVBZWIX0vufIt6I/edit?usp=sharing">Ficheiro de concepção do sistema</a>
<p>
<a href="installation-guide-tracker">Guia de Instalação</a>
   </td>
   <td><a href="https://raw.githubusercontent.com/dhis2/metadata-package-development/work-in-progress/metadata/COVID19/COVID19_TRACKER_V1_DHIS2.33/metadata.json">Ficheiro dos metadados</a>
   </td>
   <td>27 de Março de 2020
   </td>
  </tr>
  <tr>
   <td>2.33
   </td>
   <td>V 0.3.2
   </td>
   <td>Programa de Eventos de Vigilância do COVID-19
   </td>
   <td><a href="https://docs.google.com/document/d/1_OxdOmlPouNmoXD6FUEFZAgaPQARKUdrq0h0Gco4ARw/edit">Ficheiro de Concepção do Sistema</a>
<p>
<a href="installation-guide-event">Guia de Instalação</a>
   </td>
   <td> <a href="https://raw.githubusercontent.com/dhis2/metadata-package-development/work-in-progress/metadata/COVID19_EVENT/COVID19_EVENT_TRACKER_V1_DHIS2.33/metadata.json">Ficheiro dos metadados</a>
   </td>
   <td>27 de Março de 2020
   </td>
  </tr>
  <tr>
   <td>2.30
<p>
2.31
<p>
2.32
<p>
2.33
   </td>
   <td>V 0.3.2
   </td>
   <td>Vigilância agregada do COVID-19
   </td>
   <td><a href="https://docs.google.com/document/d/1My2jVCAwPVA3j9m21xp0UCti--N8am9BXsYEjI7qn3I/edit#">Ficheiro de Concepção do Sistema</a>
<p>
<a href="installation-guide-aggregate">Guia de Instalação</a>
   </td>
   <td><a href="https://raw.githubusercontent.com/dhis2/metadata-package-development/work-in-progress/metadata/COVID19_AGG/COVID19_AGG_COMPLETE_V1_DHIS2.30/metadata.json">Ficheiro dos metadados para 2.30</a>
<p>
<a href="https://raw.githubusercontent.com/dhis2/metadata-package-development/work-in-progress/metadata/COVID19_AGG/COVID19_AGG_COMPLETE_V1_DHIS2.31/metadata.json">Ficheiro dos metadados para 2.31</a>
<p>
<a href="https://raw.githubusercontent.com/dhis2/metadata-package-development/work-in-progress/metadata/COVID19_AGG/COVID19_AGG_COMPLETE_V1_DHIS2.32/metadata.json">Ficheiro dos metadados para 2.32</a>
<p>
<a href="https://raw.githubusercontent.com/dhis2/metadata-package-development/work-in-progress/metadata/COVID19_AGG/COVID19_AGG_COMPLETE_V1_DHIS2.33/metadata.json">Ficheiro dos metadados para 2.33</a>
   </td>
   <td>27 de Março de 2020
   </td>
  </tr>
  <tr>
   <td>2.33
   </td>
   <td>V 0.3.1
   </td>
   <td>Rastreador de pontos de entrada
   </td>
   <td> <a href="https://drive.google.com/open?id=1PJ4iRJGmUBv6jF7hcACxt-dhd5JRpeBt0mKxgPBsmvc">Ficheiro de Concepção do Sistema</a>
<p>
<a href="installation-guide-tracker">Guia de Instalação</a>
   </td>
   <td><a href="https://raw.githubusercontent.com/dhis2/metadata-package-development/work-in-progress/metadata/COVID19_POE/COVID19_POE_TRACKER_V1_DHIS2.33/metadata.json">Ficheiro dos metadados</a>
   </td>
   <td>27 de Março de 2020
   </td>
  </tr>
</table>

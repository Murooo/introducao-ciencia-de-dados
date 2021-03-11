# Introdução à Ciência de Dados

#### _Danilo Silva e Janderson Pereira_

## Problema a ser explorado
Compreender a dinâmica de disseminação da informação na plataforma de mídia social Twitter durante o período das eleições municipais brasileiras de 2020.

## Base de Dados
Coletada a partir das API da plataforma Twitter (REST API e STREAM API), durante o período eleitoral (26/09/2020 a 02/12/2020), com filtro para lingua portuguesa(PT), contendo os termos de busca relacionados ao contexto das eleições municipais:
`eleição, eleições, campanha, candidato, candidatos, vereador, votar, votação, voto, vereadores, prefeito, prefeitos, prefeitura, prefeituras, candidaturas, eleitoral, partidos, partido, tse, chapa, votos, vereadora, prefeita, prefeito, candidatura, eleições2020, eleição2020, eleicoes2020, vota, votou, debate`
Como resultado final, temos 71.912.648 tweets.

## Limpeza dos Dados

É possível que hajam públicacões relacionadas a outros processos eleitorais que não o brasileiro, mas que aconteceram no mesmo período temporal (principalmente elições norte-americanas). Para excluir essas publicações, utilizaremos a combinação de dois filtros:
1. Reprocessamento dos tweets em língua portuguesa utilizando a API Cloud Translation do Google;
2. Tweets criados por contas que têm o atributo `timezone` entre `GMT-5` e `GMT-2`.

Acreditamos que essa combinação de filtro pode nos assegurar que todas as publicações serão referentes ao contexto nacional.

## Experimentos

1. Identificação de automatização
* Pretendemos identificar contas que produziram publicações com um padrão claramente impossível de ser executado por um humano, como por exemplo muitos tweets no memso segundo;
* Pretendemos classificar as contas de acordo com a ferramenta de detecção de bots `Botometer
2. Identificação de polarização:
* Pretendemos, através do algoritmo de modularidade Louvain (Blondel et al., 2008) identificar subgrupos altamente conectados entre si e analisá-los
3. Identificação das contas responsáveis por difusão de informação.
* Através do conceito de cascatas de informação (Vosoughi, Roy & Aral, 2018) pretendemos identificar as contas responsáveis pela maior disseminação de conteúdo na rede, sendo ou não a conta de autoria dessa informação.
4. Identificar mudança estrutural da rede
*  Identificação de contas ativas e inativas após 4 meses do evento analisado;
*  Identificação das transitividade de usuários entre subgrupos no tempo;
*  Identificação das hashtags utilizadas por cada subgrupo no tempo;

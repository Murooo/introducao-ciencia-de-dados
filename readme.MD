'	# Introdução à Ciência de Dados

#### _Danilo Silva e Janderson Pereira_

## Problema a ser explorado
Compreender a dinâmica de disseminação da informação na plataforma de mídia social Twitter durante o período das eleições municipais brasileiras de 2020.

## Questões de Pesquisa
**Questão Principal: Há polarização no debate sobre as eleições municipais de 20202 no Twitter**

**Questões relacionadas**:
- Como se agrupam os usuários do Twitter que debatem eleições?
- Quais os períodos em que diferentes grupos se aproximam ou se afastam?


## Base de Dados
Coletada a partir das API da plataforma Twitter (REST API e STREAM API), durante o período eleitoral (26/09/2020 a 02/12/2020), com filtro para lingua portuguesa(PT), contendo os termos de busca relacionados ao contexto das eleições municipais:
`eleição, eleições, campanha, candidato, candidatos, vereador, votar, votação, voto, vereadores, prefeito, prefeitos, prefeitura, prefeituras, candidaturas, eleitoral, partidos, partido, tse, chapa, votos, vereadora, prefeita, prefeito, candidatura, eleições2020, eleição2020, eleicoes2020, vota, votou, debate`
Como resultado final, temos 71.912.648 tweets.

## Limpeza dos Dados

É possível que hajam públicacões relacionadas a outros processos eleitorais que não o brasileiro, mas que aconteceram no mesmo período temporal (principalmente elições norte-americanas). Para excluir essas publicações, utilizamos a combinação de dois filtros:
1. Reprocessamento dos tweets em língua portuguesa através do metadado de identificação de língua da publicação;
2. Tweets criados por contas que têm o atributo `timezone` entre `GMT-5` e `GMT-2`.

Após essa primeira etapa, clusterizamos os resultados e verificamos a existência de tweets não relacionados à temática analisada (tweets referentes a votações em reality shows e prêmios de música pop). As contas pertencentes a esses clusters, assim como suas publicações, foram excluídas da base de dados.

## Experimentos

1. Clusterização da base de Dados através da aplicação do algoritmo de grupabilidade Louvain (Blondel et al.,2008)
2. Análise qualitativa dos resultados da clusterização para a caracterização dos grupos
3. Análise das conexões intra e extra clusters a fim de verificar se há, de fato, indícios de polarização no debate
4. Análise temporal das conexões entre os clusters para verificar se existem períodos de intensificação de aproximação ou distanciamento dos clusters.
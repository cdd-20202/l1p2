# Mais EDA no clima de João Pessoa, Campina Grande e Patos

João Pessoa, Campina Grande e Patos são 3 referências para entender o clima na Paraíba. A primeira cidade está no litoral, a segunda próximo ao topo da Serra da Borborema, e a terceira no Sertão. Nesse exercício, você experimentará com o processo de análise exploratória dos dados usando dados dessas 3 cidades. O resultado será um relatório em RMarkdown e publicado online (instruções para publicar mais abaixo).

## As perguntas
Nesse exercício, vocês responderão 3 perguntas. Duas devem vir das perguntas abaixo, e a 3a vocês devem criar, seguindo o mesmo estilo das abaixo:

1. Considerando os meses de férias normais da UFCG e escolhendo uma das cidades (a mais próxima de onde você passa férias), quais as semelhanças e diferenças entre a temperatura e as chuvas nos meses de férias e nos meses de aula? Quando o clima é melhor? 
2. Compare a distribuição de chuvas nas 3 cidades, comparando tanto como são as semanas de muita chuva quanto com que frequência as cidades passam a semanas sem chuva.
3. Compare o quanto essas 3 cidades têm meses claramente mais quentes/frios. Em qual delas há épocas mais diferentes?

## Instruções 

Use como ponto de partida o Notebook `reports/exploracao.Rmd`. Use títulos e texto para criar um relatório que possa ser compreendido por alguém que não está no curso e que não pareça um dever de casa de um livro texto :).  Mas me ajude colocando em negrito no relatório os trechos com suas conclusões para cada pergunta.

Importante: sempre que for programar no RStudio, abra o arquivo do projeto (`l1p1.Rproj`) na raiz do repositório. Isso abre o projeto com o diretório de trabalho correto, e facilita sua vida.

### Lembre que

> A estrutura que você seguirá para cada pergunta é: (1) formular uma pergunta, (2) dizer que dados usará para responder a pergunta -- se você filtrará, transformará, etc.os originais, (3) mostrar alguma visão construída com esses dados -- geralmente uma visualização e (4) interpretar com um ou dois parágrafos de texto essa evidência.

Além disso, esse é um exercício sobre descrição de distribuições de valores **usando visualização e sumários estatísticos**. Agora já queremos agora falar em média, mediana, etc., mas lembre do datassauro e **nunca use apenas o sumário**. Queremos sempre descrever também as distribuições de valores. Use os conceitos de faixa de valores, concentração, simetria, pontos extremos e cauda para descrever cada distribuiçào que você usar. 

Atenção para dados faltantes. É importante saber o que temos e o que não temos na hora de tirar conclusões.

Mande dúvidas à vontade nos canais públicos do slack. Assim todos nos ajudamos.

## Submissão

Há dois resultados desse exercício que serão avaliados:

* O código que está no seu repositório no final do prazo
* O link do seu relatório [em html publicado no rpubs](https://rpubs.com/about/getting-started) que deve ser enviado no google classroom.

Repare que o código não precisa ser submetido. Basta deixá-lo atualizado. 

## Os dados

Dados vêm do BDMEP: https://tempo.inmet.gov.br/ . Selecionei lá a estação convencional em João Pessoa, Campina Grande e Patos - PB, e baixei os csvs com dados desde 2010. 

Os dados brutos estão em `data/raw`. O código em `transform` faz ETL e o coloca em `data/`. Você não usará os dados raw, mas é bom saber de onde eles vêm.

No processo de ETL, calculamos as variáveis de interesse por semana. Isso porque há bastante medições vazias nas estações, e queremos deixar o dado mais fácil de ser trabalhado. Mas ainda há várias semanas onde alguma ou todas as medidas são NA.

Cada item nos dados é uma medição das condições de clima em uma semana em uma cidade. As colunas que cada item tem são as seguintes:

```
$ cidade      <chr> A cidade da medição
$ semana      <date> O primeiro dia da semana à qual a medição se refere
$ temp_max    <dbl> A maior temperatura máxima diária registrada nessa semana, em Celsius
$ temp_media  <dbl> A média das temperaturas médias diárias da semana, em Celsius
$ temp_min    <dbl> Menor temperatura registrada nessa semana, em Celsius
$ vento_medio <dbl> Média da velocidade do vento ao longo da semana, em m/s.
$ vento_max   <dbl> Maior velocidade média diária do vento ao longo da semana, em m/s.
$ umidade     <dbl> Médiia da umidade diária na semana, em %
$ chuva       <dbl> Total de precipicação na semana, em mm.
```

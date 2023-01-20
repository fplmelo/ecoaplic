---
title: "Aula 4 - Tabelas de vida e estrutura etária"
author: "Felipe Melo"
date: ""
output: html_document
---

# Slides dessa aula [AQUI](https://ecoaplic.org/slides_aulas/eco_geral1/04_tabelas_vida.html#1)

<img src = https://www.nature.com/scitable/content/ne0000/ne0000/ne0000/ne0000/83033266/1_2.jpg >

<br>

## Estrutura etária
Entender a estrutura etária de uma população é fundamental para compreender suas taxas de crescimento e mortalidade bem como modelar o que poderá acontecer com populações no futuro. Estrutura pode ser repartida em "componentes" e "configurações". Os componentes de uma populaçõa são a quantidade de indívudos e sua configuração é a que estágio ontogenético (classe etária) ou sexo pertencem os indivíduos. Não todos os indivíduos de uma população são reprodutivos por cuasa por idade ou sexo. Da mesma forma, nem todos os indivíduos de uma população têm a mesma proabilidad de morrer, também determinada por sexo e idade. 

## Pirâmide etária

<iframe width="700" height="400" src="https://www.youtube.com/embed/UPgR_LL0Fz0" title="Pirâmide etária: uma viagem no tempo pelas características da população brasileira • IBGE Explica" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

No video acima, você pode entender como no IBGE a pirâmide etária é usada para entender a demografia do Brasil. Na ecologia de populações usamos os mesmos princípios para entender a dinâmica de populações silvestres de planas e animais. Essas ferramentas tem grande potencial para diversas atvidades humanas. Você é capaz de citar algumas aplicações desses conceitos e ferramentas para a agricultura, conservação da biodiversidade, pesca? (veja exercícios abaixo)

## Tabelas de vida

As tabelas de vida expressam a probabilidade de mortalidade em diferentes classes etárias e portanto, quantos indivíduos passarão de uma classe à seguinte. São tabelas relativamente simples que fornecem informações impotantes e complementares às pimâmides etárias. 

![](/collection/ecogeral1/03_crescimento populacional/03_crescimento_populacional_files/tabela.png)

### Parâmetros das tabela de vida

Tabala 1. Tabela de vida hipotética de um inseto com fases 4 fases larvais. 

| Faixa etária | Sobreviventes | Prop de Sobreviventes | Prole total | Prole/Ind | Prole/Sobreviventes |
|--|--|--|--|--|--|
|x | a<sub>x</sub> | l<sub>x</sub> | F<sub>x</sub> | m<sub>x</sub> | l<sub>x</sub>*m<sub>x</sub>| 
|Ovos (x=0)|10000|1|-|-|-|
|Instar 1 (x=1)|800|0,08|-|-|-|
|Instar 2 (x=2)|500|0,05|-|-|-|
|Instar 3 (x=3)|450|0,045|-|-|-|
|Instar 4 (x=4)|400|0,04|-|-|-|
|Adultos (x=5)|350|0,035|8000|22,8|0,8|

A fórmula para calcular a taxa de crescimento líquida de uma população se calcula pela expressão abaixo

$$
R_0=\sum l_xm_x=\frac {\sum F_x }{a_0} = \frac{8000}{10000} = 0,8
$$

Os parâmetros de mortalidade, expressados por: número de mortos (d<sub>x</sub>), taxa de mortalidade (q<sub>x</sub>) e força da mortalidade (killing power k<sub>x</sub> ou log<sub>10</sub>(a<sub>x</sub>/a<sub>x+1</sub>)).

| Faixa etária | Sobreviventes| Mortalidade | Prop de mortos | "Killing power" | Prole/Sobreviventes |
|--|--|--|--|--|--|
|x | a<sub>x</sub> | d<sub>x</sub> | q<sub>x</sub> | k<sub>x</sub> | F<sub>x</sub>| 
|Ovos (x=0)|10000|9200|0,92|1,09|-|
|Instar 1 (x=1)|800|300|37,5|0,2|-|
|Instar 2 (x=2)|500|50|0,10|0,045 |-|
|Instar 3 (x=3)|450|50|0,11|0,05|-|
|Instar 4 (x=4)|400|50|0,125|0,057|-|
|Adultos (x=5)|350|350|1|22,8|0,8|

Com esses dados é possível modelar a dinâmica de qualquer população e inclusive comparar populações diferentes pois muitos dos parâmetros por se tratarem de uma taxa normalizada podem ser usados em comparações mesmo com valores absolutos muito diferentes entre populações.

Em resumo, temos:
| Parâmetro | Defnição| 
|--|--|
|x| Estágio de vida ou clsse etária ou estágio ontogenético ou tamanho...|
|a<sub>x</sub>| Número de indivíduos observadosem cada classe de "x" |
|l<sub>x</sub>| Taxa de sobreviventes ou proporção de indivíduos que passa de x a x+1 |
|d<sub>x</sub>| Mortalidade ou  número de indivíduos que não sobrevive a cada geração "x"|
|q<sub>x</sub>| Taxa de mortalidade, ou proportção de indivíduos mortos para cada classe de "x"|
|k<sub>x</sub>| Força da mortalidade ou "killing power", representada pela razão logaritimzada dos parâmtetros de sobrevivência entre x e x+1|
|F<sub>x</sub>| Fecundidade total ou número de proles deixado por cada estágio de "x"|
|m<sub>x</sub>| Fecundidade por indivíduo, portanto normalizada pelo número de indivíduos da populção em cada estágio "x"|
|l<sub>x</sub>*m<sub>x</sub>| Taxa de repordução por sobrevivente |
|Rl<sub>0</sub>| Taxa reprodutiva líquida|


### Curvas de sobreviência

<img src=https://cdn.britannica.com/42/6542-050-B6E0E2B9/survivorship-curve-II-Type-I-curves-III.jpg>

As curvas de sobrevivência são a representação gráfica de parâmetros selecionados de uma tabela de vida e refletem como a população evolui no seu desonvolvimento ontogenético (idade).

Os três tipos básicos de survas de sobrevivência são os representados na figura acima.

#### Pergunta: Você seria capaz de pensar em implicações práticas para o manejo de espécies (exploração comercial, conservação, reintrodução, controle de invasoras) derivados de curvas de sobrevivência?



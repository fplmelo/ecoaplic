---
title: "Beta-diversidade"
author: "Felipe Melo"
date: "02 de março"
output: html_document
---

<script src="/rmarkdown-libs/fitvids/fitvids.min.js"></script>

<img src = https://www.davidzeleny.net/anadat-r/lib/exe/fetch.php/obrazky:jurasinsky_et_al_diversity_schema_350.png>

<br>

<div class="shareagain" style="min-width:300px;margin:1em auto;" data-exeternal="1">
<iframe src="https://ecoaplic.org/slides_aulas/slides_eco_num/beta_diversidade.html#1" width="1600" height="900" style="border:2px solid currentColor;" loading="lazy" allowfullscreen></iframe>
<script>fitvids('.shareagain', {players: 'iframe'});</script>
</div>

# Beta diversidade é medir diferença entre comunidades

## Exemplo

## Vamos usar os dados de um artigo em que participei para medir a diverisdade beta dentro de paisagens com diferentes graus de desmatamento.

### **Plant β-diversity in fragmented rain forests: testing floristic homogenization and differentiation hypotheses**

https://doi.org/10.1111/1365-2745.12153

<img src= https://besjournals.onlinelibrary.wiley.com/cms/asset/1dbf3022-ce72-4ccf-861c-2a7f691daa06/jec12153-fig-0001-m.jpg>

Nessa figura vemos as paisagens estudadas. São três, LDL, IDL e HDL. Elas se diferenciam pelo grau de desmatamento que cada uma apresenta. LDL = LOW deforestain level, IDL = INTERMEDIATE deforestation level e HDL = HIGH deforestaion level.

Portanto, é um gradiente ambiental de desmatamento sobre o qual testamos se essa variável causava **homogenização** ou **dierenciaçãp** florística na paisagem. Portanto estávemos interessados sobre como a diversidade beta variava em função desse gradiente.

Mas, para os fins desse exercício, vamos apenas *brincar* com a beta-diversidade.

``` r
dados<-read.csv("https://raw.githubusercontent.com/fplmelo/ecoa/main/content/en/courses/eco_num/betadiv/com_ltx_all.csv", row.names = "X")
dados<-as.data.frame(dados)
dim(dados) # note que em vez de 45 plots, 15 para cada paisagem, temos apenas 36 plots porque alugns forma excluídos por baixa cobertura.
```

    ## [1] 179  36

Passo 1) Calcular a Alfa uando o “entropart”

``` r
mc<-MetaCommunity(dados)
# head(mc) descomente essa somente se quiser ver o output

AlphaDiversity(mc, q=0, Correction = "None") # use sempre correction "None" para não gerar números diferentes
```

    ## $MetaCommunity
    ## [1] "mc"
    ## 
    ## $Method
    ## [1] "Neutral"
    ## 
    ## $Type
    ## [1] "alpha"
    ## 
    ## $Order
    ## [1] 0
    ## 
    ## $Correction
    ## [1] "None"
    ## 
    ## $Normalized
    ## [1] TRUE
    ## 
    ## $Weights
    ##       LDL1       LDL3       LDL4       LDL5       LDL8       LDL9      LDL10 
    ## 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 
    ##      LDL11      LDL12      LDL13      LDL14      LDL15       IDL1       IDL4 
    ## 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 
    ##       IDL5       IDL6       IDL7       IDL8       IDL9      IDL10      IDL11 
    ## 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 
    ##      IDL12      IDL13      IDL14      IDL15       HDL2       HDL3       HDL4 
    ## 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 
    ##       HDL5       HDL6      HDL10      HDL11      HDL12      HDL13      HDL14 
    ## 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 
    ##      HDL15 
    ## 0.02777778 
    ## 
    ## $Communities
    ##  LDL1  LDL3  LDL4  LDL5  LDL8  LDL9 LDL10 LDL11 LDL12 LDL13 LDL14 LDL15  IDL1 
    ##    35    30    30    29    38    40    26    32    36    27    36    23    38 
    ##  IDL4  IDL5  IDL6  IDL7  IDL8  IDL9 IDL10 IDL11 IDL12 IDL13 IDL14 IDL15  HDL2 
    ##    31    31    32    38    29    41    32    27    40    40    35    46    38 
    ##  HDL3  HDL4  HDL5  HDL6 HDL10 HDL11 HDL12 HDL13 HDL14 HDL15 
    ##    40    25    26    25    27    15    18    21    39    29 
    ## 
    ## $Total
    ## [1] 31.80556
    ## 
    ## attr(,"class")
    ## [1] "MCdiversity"

``` r
AlphaDiversity(mc, q=1, Correction = "None")
```

    ## $MetaCommunity
    ## [1] "mc"
    ## 
    ## $Method
    ## [1] "Neutral"
    ## 
    ## $Type
    ## [1] "alpha"
    ## 
    ## $Order
    ## [1] 1
    ## 
    ## $Correction
    ## [1] "None"
    ## 
    ## $Normalized
    ## [1] TRUE
    ## 
    ## $Weights
    ##       LDL1       LDL3       LDL4       LDL5       LDL8       LDL9      LDL10 
    ## 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 
    ##      LDL11      LDL12      LDL13      LDL14      LDL15       IDL1       IDL4 
    ## 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 
    ##       IDL5       IDL6       IDL7       IDL8       IDL9      IDL10      IDL11 
    ## 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 
    ##      IDL12      IDL13      IDL14      IDL15       HDL2       HDL3       HDL4 
    ## 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 
    ##       HDL5       HDL6      HDL10      HDL11      HDL12      HDL13      HDL14 
    ## 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 
    ##      HDL15 
    ## 0.02777778 
    ## 
    ## $Communities
    ##      LDL1      LDL3      LDL4      LDL5      LDL8      LDL9     LDL10     LDL11 
    ## 27.222539 25.629042 22.941212 24.387995 25.468065 29.897721  7.311644 21.888908 
    ##     LDL12     LDL13     LDL14     LDL15      IDL1      IDL4      IDL5      IDL6 
    ## 29.349849 24.342215 25.964012 13.197723 30.755277 24.461617 19.699180 25.450513 
    ##      IDL7      IDL8      IDL9     IDL10     IDL11     IDL12     IDL13     IDL14 
    ## 25.265590 23.159886 25.854673 27.138127 18.074630 30.816146 33.977934 21.894257 
    ##     IDL15      HDL2      HDL3      HDL4      HDL5      HDL6     HDL10     HDL11 
    ## 35.997088 31.969923 30.800462 20.816537 17.365476 20.844865 20.562416  6.173823 
    ##     HDL12     HDL13     HDL14     HDL15 
    ## 11.350338 17.717858 31.130084 21.344945 
    ## 
    ## $Total
    ## [1] 22.28671
    ## 
    ## attr(,"class")
    ## [1] "MCdiversity"

``` r
AlphaDiversity(mc, q=2, Correction = "None")
```

    ## $MetaCommunity
    ## [1] "mc"
    ## 
    ## $Method
    ## [1] "Neutral"
    ## 
    ## $Type
    ## [1] "alpha"
    ## 
    ## $Order
    ## [1] 2
    ## 
    ## $Correction
    ## [1] "None"
    ## 
    ## $Normalized
    ## [1] TRUE
    ## 
    ## $Weights
    ##       LDL1       LDL3       LDL4       LDL5       LDL8       LDL9      LDL10 
    ## 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 
    ##      LDL11      LDL12      LDL13      LDL14      LDL15       IDL1       IDL4 
    ## 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 
    ##       IDL5       IDL6       IDL7       IDL8       IDL9      IDL10      IDL11 
    ## 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 
    ##      IDL12      IDL13      IDL14      IDL15       HDL2       HDL3       HDL4 
    ## 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 
    ##       HDL5       HDL6      HDL10      HDL11      HDL12      HDL13      HDL14 
    ## 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 
    ##      HDL15 
    ## 0.02777778 
    ## 
    ## $Communities
    ##      LDL1      LDL3      LDL4      LDL5      LDL8      LDL9     LDL10     LDL11 
    ## 20.353846 21.446602 17.147783 20.578231 17.963124 21.690323  3.275528 13.986877 
    ##     LDL12     LDL13     LDL14     LDL15      IDL1      IDL4      IDL5      IDL6 
    ## 23.485207 22.153846 18.558185  8.125604 24.557604 20.374570 13.586621 20.433476 
    ##      IDL7      IDL8      IDL9     IDL10     IDL11     IDL12     IDL13     IDL14 
    ## 17.016807 18.788820 16.346687 23.684444 12.686792 23.837838 28.285714 11.479245 
    ##     IDL15      HDL2      HDL3      HDL4      HDL5      HDL6     HDL10     HDL11 
    ## 27.842105 26.560976 23.040134 17.899408 11.505618 17.344262 14.727273  3.835894 
    ##     HDL12     HDL13     HDL14     HDL15 
    ##  8.294931 14.520000 25.137931 17.192837 
    ## 
    ## $Total
    ## [1] 14.11629
    ## 
    ## attr(,"class")
    ## [1] "MCdiversity"

Passo 2) Calcular a Beta uando o “entropart”

``` r
BetaDiversity(mc, q=0, Correction = "None") # use sempre correction "None" para não gerar números diferentes
```

    ## $MetaCommunity
    ## [1] "mc"
    ## 
    ## $Method
    ## [1] "Neutral"
    ## 
    ## $Type
    ## [1] "beta"
    ## 
    ## $Order
    ## [1] 0
    ## 
    ## $Correction
    ## [1] "None"
    ## 
    ## $Normalized
    ## [1] TRUE
    ## 
    ## $Weights
    ##       LDL1       LDL3       LDL4       LDL5       LDL8       LDL9      LDL10 
    ## 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 
    ##      LDL11      LDL12      LDL13      LDL14      LDL15       IDL1       IDL4 
    ## 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 
    ##       IDL5       IDL6       IDL7       IDL8       IDL9      IDL10      IDL11 
    ## 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 
    ##      IDL12      IDL13      IDL14      IDL15       HDL2       HDL3       HDL4 
    ## 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 
    ##       HDL5       HDL6      HDL10      HDL11      HDL12      HDL13      HDL14 
    ## 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 
    ##      HDL15 
    ## 0.02777778 
    ## 
    ## $Total
    ## [1] 5.627948
    ## 
    ## attr(,"class")
    ## [1] "MCdiversity"

``` r
BetaDiversity(mc, q=1, Correction = "None")
```

    ## $MetaCommunity
    ## [1] "mc"
    ## 
    ## $Method
    ## [1] "Neutral"
    ## 
    ## $Type
    ## [1] "beta"
    ## 
    ## $Order
    ## [1] 1
    ## 
    ## $Correction
    ## [1] "None"
    ## 
    ## $Normalized
    ## [1] TRUE
    ## 
    ## $Weights
    ##       LDL1       LDL3       LDL4       LDL5       LDL8       LDL9      LDL10 
    ## 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 
    ##      LDL11      LDL12      LDL13      LDL14      LDL15       IDL1       IDL4 
    ## 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 
    ##       IDL5       IDL6       IDL7       IDL8       IDL9      IDL10      IDL11 
    ## 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 
    ##      IDL12      IDL13      IDL14      IDL15       HDL2       HDL3       HDL4 
    ## 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 
    ##       HDL5       HDL6      HDL10      HDL11      HDL12      HDL13      HDL14 
    ## 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 
    ##      HDL15 
    ## 0.02777778 
    ## 
    ## $Total
    ## [1] 4.25749
    ## 
    ## attr(,"class")
    ## [1] "MCdiversity"

``` r
BetaDiversity(mc, q=2, Correction = "None")
```

    ## $MetaCommunity
    ## [1] "mc"
    ## 
    ## $Method
    ## [1] "Neutral"
    ## 
    ## $Type
    ## [1] "beta"
    ## 
    ## $Order
    ## [1] 2
    ## 
    ## $Correction
    ## [1] "None"
    ## 
    ## $Normalized
    ## [1] TRUE
    ## 
    ## $Weights
    ##       LDL1       LDL3       LDL4       LDL5       LDL8       LDL9      LDL10 
    ## 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 
    ##      LDL11      LDL12      LDL13      LDL14      LDL15       IDL1       IDL4 
    ## 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 
    ##       IDL5       IDL6       IDL7       IDL8       IDL9      IDL10      IDL11 
    ## 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 
    ##      IDL12      IDL13      IDL14      IDL15       HDL2       HDL3       HDL4 
    ## 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 
    ##       HDL5       HDL6      HDL10      HDL11      HDL12      HDL13      HDL14 
    ## 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 0.02777778 
    ##      HDL15 
    ## 0.02777778 
    ## 
    ## $Total
    ## [1] 4.419122
    ## 
    ## attr(,"class")
    ## [1] "MCdiversity"

Passo 3) Calcular a Gama uando o “entropart”

``` r
GammaDiversity(mc, q=0, Correction = "None") # use sempre correction "None" para não gerar números diferentes
```

    ## None 
    ##  179

``` r
GammaDiversity(mc, q=1, Correction = "None")
```

    ##     None 
    ## 94.88546

``` r
GammaDiversity(mc, q=2, Correction = "None")
```

    ##     None 
    ## 62.38163

Passo 4) Gerar um perfil de diversidade

``` r
Profile <- DivProfile(q.seq = seq(0, 2, 0.1), mc, Biased = FALSE, Correction = "None")
plot(Profile)
```

<img src="/collection/eco_num/betadiv/betadiv_files/figure-html/unnamed-chunk-6-1.png" width="672" />

``` r
summary(Profile)
```

    ## Diversity profile of MetaCommunity mc
    ##  with correction: None
    ## Diversity against its order:
    ##      Order Alpha Diversity Beta Diversity Gamma Diversity
    ## None   0.0        31.80556       5.627948       179.00000
    ## None   0.1        30.85554       5.417085       167.14707
    ## None   0.2        29.89974       5.221463       156.12037
    ## None   0.3        28.93997       5.041821       145.91015
    ## None   0.4        27.97820       4.878732       136.49813
    ## None   0.5        27.01649       4.732591       127.85800
    ## None   0.6        26.05700       4.603608       119.95622
    ## None   0.7        25.10198       4.491810       112.75332
    ## None   0.8        24.15370       4.397063       106.20534
    ## None   0.9        23.21450       4.319087       100.26545
    ## None   1.0        22.28671       4.257490        94.88546
    ## None   1.1        21.37266       4.211794        90.01725
    ## None   1.2        20.47465       4.181460        85.61391
    ## None   1.3        19.59491       4.165909        81.63063
    ## None   1.4        18.73564       4.164541        78.02535
    ## None   1.5        17.89891       4.176742        74.75913
    ## None   1.6        17.08668       4.201890        71.79636
    ## None   1.7        16.30077       4.239354        69.10475
    ## None   1.8        15.54282       4.288491        66.65526
    ## None   1.9        14.81427       4.348641        64.42193
    ## None   2.0        14.11629       4.419122        62.38163

Passo 5) Agora é com vocês e o pacote betapart. A intenção aqui é entender a contribuição dos componentes de “aninhamento” e “substituição de espécies” de cada paisagem. Vou fazer abaixo pra uma delas, LDL

``` r
dadosLDL<-dados[, 1:12]
dadosLDL<-ifelse(dadosLDL=="0",0,1) # Tranformei em 0 e 1

beta.core<-betapart.core(dadosLDL)
beta.multi<-beta.multi(dadosLDL)
beta.multi # Aquei stão os valores... interprete
```

    ## $beta.SIM
    ## [1] 0.9543153
    ## 
    ## $beta.SNE
    ## [1] 0.03262383
    ## 
    ## $beta.SOR
    ## [1] 0.9869392

Passo 6) Faça o mesmo para as outras dus paisagens, interprete e grafique como quiser. Escreva sua interpretação no seu Rmarkdown e coloque no exercício.

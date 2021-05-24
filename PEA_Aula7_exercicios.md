Probabilidade e Estatística - Aula 7
================
Rogério de Oliveira
2021-05-24

# Regressão Linear

-----

<img src="http://meusite.mackenzie.br/rogerio/mackenzie_logo/UPM.2_horizontal_vermelho.jpg"  width=300, align="right">
<br> <br> <br> <br> <br>

## Exercícios

### Exercício 1

Considere a base.

``` r
require(stats)
head(stackloss)
```

    ##   Air.Flow Water.Temp Acid.Conc. stack.loss
    ## 1       80         27         89         42
    ## 2       80         27         88         37
    ## 3       75         25         90         37
    ## 4       62         24         87         28
    ## 5       62         22         87         18
    ## 6       62         23         87         18

``` r
help(stackloss)
```

    ## starting httpd help server ... done

1.  Qual a função linear que melhor aproxima `stack.loss` com base nos
    demais valores? **Solução**

2.  Faça uma predição do valor de `stock.loss` para os valores de
    `Air.Flow=72, Water.Temp=20, Acid.Conc=85`.

**Solução**

3.  A instância `Air.Flow=72, Water.Temp=20, Acid.Conc=85` está presente
    na base. Quanto o valor obtido pelo modelo esse valor difere do
    valor encontrado na base?

**Solução**

4.  QUal atributo contribui mais positivamente para o incremento de
    stackloss?

Isso pode ser identificado pelo coeficiente associado ao atributo
(coeficientes maiores tem um efeito maior). Entretanto, as variáveis
encontram-se em escalas diferentes e, portanto, você precisa normalizar
os dados antes de observar os coeficientes da regressão. Você pode
empregar a função abaixo para uma normalização min-max (levando todos
valores de cada atributo ao intervalo \[0,1\]).

``` r
normalize <- function(x) {
return ((x - min(x)) / (max(x) - min(x)))
}
  
stack_n = as.data.frame(lapply(stackloss, normalize))
summary(stack_n)
```

    ##     Air.Flow        Water.Temp       Acid.Conc.       stack.loss    
    ##  Min.   :0.0000   Min.   :0.0000   Min.   :0.0000   Min.   :0.0000  
    ##  1st Qu.:0.2000   1st Qu.:0.1000   1st Qu.:0.4762   1st Qu.:0.1143  
    ##  Median :0.2667   Median :0.3000   Median :0.7143   Median :0.2286  
    ##  Mean   :0.3476   Mean   :0.4095   Mean   :0.6803   Mean   :0.3007  
    ##  3rd Qu.:0.4000   3rd Qu.:0.7000   3rd Qu.:0.8095   3rd Qu.:0.3429  
    ##  Max.   :1.0000   Max.   :1.0000   Max.   :1.0000   Max.   :1.0000

**Solução**

5.  A regressão linear obtida é uma boa aproximação dos dados (R-squared
    \> 0.85)? Qual o valor do (Multiple) R-squared obtido?

**Solução**

### Exercício 2

Considere o exercício anterior. Elimine o atributo que não é
significativo para a regressão e recalcule.

**Dica**: verifique o p-value dos coeficientes.

1.  Qual o novo valor do (Multiple) R-squared obtido?
2.  Qual a função linear obtida?

**Solução**

3.  Modelos com com menos variáveis preditoras são modelos preferíveis
    pois assumem uma menor quantidade de hipóteses sobre os dados
    (procure na Internet, Occam’s razor ou princípio da parcimônia).
    Sendo a diferença do (Multiple) R-squared obtido no exercício
    anterior e nesta agora menor que 5%, este agora é um modelo melhor?

**Solução**

### Exercício 3

Considere a base.

``` r
df = read.csv('https://meusite.mackenzie.br/rogerio/TIC/FuelConsumptionCo2.csv',header=T)
head(df)
```

    ##   MODELYEAR  MAKE      MODEL VEHICLECLASS ENGINESIZE CYLINDERS TRANSMISSION
    ## 1      2014 ACURA        ILX      COMPACT        2.0         4          AS5
    ## 2      2014 ACURA        ILX      COMPACT        2.4         4           M6
    ## 3      2014 ACURA ILX HYBRID      COMPACT        1.5         4          AV7
    ## 4      2014 ACURA    MDX 4WD  SUV - SMALL        3.5         6          AS6
    ## 5      2014 ACURA    RDX AWD  SUV - SMALL        3.5         6          AS6
    ## 6      2014 ACURA        RLX     MID-SIZE        3.5         6          AS6
    ##   FUELTYPE FUELCONSUMPTION_CITY FUELCONSUMPTION_HWY FUELCONSUMPTION_COMB
    ## 1        Z                  9.9                 6.7                  8.5
    ## 2        Z                 11.2                 7.7                  9.6
    ## 3        Z                  6.0                 5.8                  5.9
    ## 4        Z                 12.7                 9.1                 11.1
    ## 5        Z                 12.1                 8.7                 10.6
    ## 6        Z                 11.9                 7.7                 10.0
    ##   FUELCONSUMPTION_COMB_MPG CO2EMISSIONS
    ## 1                       33          196
    ## 2                       29          221
    ## 3                       48          136
    ## 4                       25          255
    ## 5                       27          244
    ## 6                       28          230

1.  Construa um modelo de regressão para:

e faça o gráfico da regressão obtida mostrando a aproximação com os
dados.

1.  Qual o valor do (Multiple) R-squared obtido?

**Solução**

2.  Estime as emissões de CO2EMISSIONS a partir de valores de
    FUELCONSUMPTION\_COMB para os valores 10 e 25. Quais os valores
    obtidos?

**Solução**

3.  Acrescente ao seu modelo a variável de entrada ENGINESIZE.

3.1. Qual a função linear obtida? 3.2. Qual o novo valor do (Multiple)
R-squared obtido? Esse é um modelo melhor que o anterior?

**Solução**

4.  Faça agora a predição de CO2EMISSIONS com base no modelo anterior,
    para `FUELCONSUMPTION_COMB = 10` e `ENGINESIZE=2`. Qual o valor
    encontrado?

**Solução**

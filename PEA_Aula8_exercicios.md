Regressão Logística
===================

------------------------------------------------------------------------

<img src="http://meusite.mackenzie.br/rogerio/mackenzie_logo/UPM.2_horizontal_vermelho.jpg"  width=300, align="right">
<br> <br> <br> <br> <br>

Exercícios
----------

### Exercício 1

1.  Crie um modelo de regressão logística para classificar os veículos
    de `mtcars` como automáticos e não automáticos (atributo `am`),
    tendo como base as variáveis preditoras `hp`, e peso, `wt`. É o
    mesmo que criamos no material de teoria, mas agora, tente criar o
    modelo por conta própria!

**Solução**

1.  Empregue o modelo obtido para fazer predição de TODOS os veículos de
    `mtcars`. Compare os valores da predição com os valores reais da
    base. Verifique o número de acertos e erros do modelo.

<!-- -->

1.  Quantos veículos classificados corretamente?
2.  Qual o percentual de acerto?

**Solução**

### Exercício 2

Empregue agora a base de dados Cars93.

``` r
library(MASS)
head(Cars93)
```

    ##   Manufacturer   Model    Type Min.Price Price Max.Price MPG.city MPG.highway
    ## 1        Acura Integra   Small      12.9  15.9      18.8       25          31
    ## 2        Acura  Legend Midsize      29.2  33.9      38.7       18          25
    ## 3         Audi      90 Compact      25.9  29.1      32.3       20          26
    ## 4         Audi     100 Midsize      30.8  37.7      44.6       19          26
    ## 5          BMW    535i Midsize      23.7  30.0      36.2       22          30
    ## 6        Buick Century Midsize      14.2  15.7      17.3       22          31
    ##              AirBags DriveTrain Cylinders EngineSize Horsepower  RPM
    ## 1               None      Front         4        1.8        140 6300
    ## 2 Driver & Passenger      Front         6        3.2        200 5500
    ## 3        Driver only      Front         6        2.8        172 5500
    ## 4 Driver & Passenger      Front         6        2.8        172 5500
    ## 5        Driver only       Rear         4        3.5        208 5700
    ## 6        Driver only      Front         4        2.2        110 5200
    ##   Rev.per.mile Man.trans.avail Fuel.tank.capacity Passengers Length Wheelbase
    ## 1         2890             Yes               13.2          5    177       102
    ## 2         2335             Yes               18.0          5    195       115
    ## 3         2280             Yes               16.9          5    180       102
    ## 4         2535             Yes               21.1          6    193       106
    ## 5         2545             Yes               21.1          4    186       109
    ## 6         2565              No               16.4          6    189       105
    ##   Width Turn.circle Rear.seat.room Luggage.room Weight  Origin          Make
    ## 1    68          37           26.5           11   2705 non-USA Acura Integra
    ## 2    71          38           30.0           15   3560 non-USA  Acura Legend
    ## 3    67          37           28.0           14   3375 non-USA       Audi 90
    ## 4    70          37           31.0           17   3405 non-USA      Audi 100
    ## 5    69          39           27.0           13   3640 non-USA      BMW 535i
    ## 6    69          41           28.0           16   2880     USA Buick Century

Crie então modelos de regressão logística para classificar a origem dos
veículos.

1.  Crie um modelo de regressão logística para classificar a origem dos
    veículos a partir dos valores de `Price`, `Weight` e `Length`, e
    responda:

1.1. Qual atributo apresenta coeficiente com pouca significância?

\*\* Dica \*\* Certifique-se de não haverem dados ausentes a serem
empregados na regressão. Você precisará também converter o atributo
objetivo para numérico, 1 e 0, ou adicionar um novo campo para isso.

**Solução**

1.2. Retire o atributo que apresenta o coeficiente da regressão com
pouca significância e recrie o modelo sem ele. Em princípio esse será um
modelo com menos hipóteses e portanto melhor. Todos os coeficientes
apresentam agora p-value \< 0.05 (são portanto significativos)? Qual
atributo apresenta menor p-value?

**Solução**

1.3. Faça agora, com o modelo construído, uma predição da origem dos
veículos com as características abaixo. Qual a origem estimada de cada
veículo?

    ##   Price Length
    ## 1    17    150
    ## 2    19    170
    ## 3    21    190

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

``` r
table(df$FUELTYPE)
```

    ## 
    ##   D   E   X   Z 
    ##  27  92 514 434

1.  Crie um modelo logístico para classificar os veículos, com base nos
    dados de consumo de combinado de combustível FUELCONSUMPTION\_COMB e
    emissões CO2EMISSIONS, em veículos de gasolina especial ‘X’ e demais
    combustíveis (atributo FUELTYPE).

**Dica** FUELTYPE tem mais de dois valores e a regressão logística
somente pode classificar em combustível ‘X’ ou não ‘X’. Crie um novo
atributo FUELX, com 1 se ‘X’ ou 0 caso contrário, e faça a regressão
logística sobre esse valor.

1.1. Todos os coeficientes são significativos? **Solução**

1.2. Estime a probabilidade (na verdade a ‘chance logística’, isto é o
valor de retorno da função logística) de um veículo com
‘FUELCONSUMPTION\_COMB’=9, ‘CO2EMISSIONS’=180 ser um veículo de gasolina
especial ‘X’.

**solução**

1.3. Empregue o seu modelo e obtenha a predição para todos os veículos
da base. Compare os valores da predição com os valores reais da base.
Verifique o número de acertos e erros do modelo. Qual percentual de
acerto? (responda o valor entre 0 e 1, isto é 60% = 0.6)

**Solução**

1.4. Adicione ao modelo os atributos ENGINESIZE e CYLINDERS e compare
novamente os valores da predição com os valores reais da base. Qual
percentual de acerto agora? (responda o valor entre 0 e 1, isto é 60% =
0.6)

**Solução**

### Exercício 4

Considere a base.

``` r
library(MASS)
help("biopsy")
```

    ## starting httpd help server ... done

``` r
bio = na.omit(biopsy[,-c(1)]) # 1 = ID
bio$class = as.numeric(bio$class) - 1 
head(bio)
```

    ##   V1 V2 V3 V4 V5 V6 V7 V8 V9 class
    ## 1  5  1  1  1  2  1  3  1  1     0
    ## 2  5  4  4  5  7 10  3  2  1     0
    ## 3  3  1  1  1  2  2  3  1  1     0
    ## 4  6  8  8  1  3  4  3  7  1     0
    ## 5  4  1  1  3  2  1  3  1  1     0
    ## 6  8 10 10  8  7 10  9  7  1     1

Implemente um modelo logístico para classificação “benign” ou
“malignant” das instâncias de bio. Compare os valores da sua predição
com os valores reais da base.

Dica: para usar todos os atributos de entrada empregue ‘.’ no lugar das
variáveis de entrada.

**Solução**

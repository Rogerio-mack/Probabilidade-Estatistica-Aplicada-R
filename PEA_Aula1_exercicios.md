Probabilidade, Estatística e Introdução ao R
============================================

------------------------------------------------------------------------

<img src="http://meusite.mackenzie.br/rogerio/mackenzie_logo/UPM.2_horizontal_vermelho.jpg"  width=300, align="right">
<br> <br> <br> <br> <br>

Exercícios
----------

### Exercício 1

Considere a base.

``` r
df = read.csv('http://meusite.mackenzie.br/rogerio/TIC/mystocksn.csv')
head(df)
```

    ##         data   IBOV VALE3 PETR4  DOLAR
    ## 1 2020-01-02 118573 13.45 16.27 4.0163
    ## 2 2020-01-03 117707 13.29 15.99 4.0234
    ## 3 2020-01-06 116878 13.14 16.22 4.0570
    ## 4 2020-01-07 116662 13.23 16.06 4.0604
    ## 5 2020-01-08 116247 13.22 15.70 4.0662
    ## 6 2020-01-09 115947 12.99 15.75 4.0628

1.  Inspecione os dados. Quantos registros e quantidade de atributos,
    quais atributos, etc. Qual o valor mínimo e máximo do dólar neste
    período?

**Solução**

1.  Forneça as principais estatísticas dos dados com `summary`.

**Solução**

1.  Crie um dataframe `mydf` somente com data e os índices VALE3 e
    PETR4.

**Solução**

1.  Qual o valor da ação VALE3 em 2020-03-02?

**Solução**

1.  Qual a média de valor da ação VALE3 nos dados?

**Solução**

1.  Quantas vezes no período a ação VALE3 esteve acima da média para o
    mesmo período?

**Solução**

1.  Qual o percentual de vezes no período que a ação VALE3 esteve acima
    da média?

**Solução**

1.  Em algum momento no período a ação da VALE3 esteve com preço maior
    que a PETR4? Se sim, em que datas?

**Solução**

### Exercício 2

Considere a base.

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

1.  Quais são os tipos (`Type`) de veículos existentes? Qual o que
    apresenta maior número de veículos?

**Solução**

1.  Qual média de potência (`Horsepower`) dos veículos de Cars93 por
    origem?

DICA: verifique antes os valores de origem com `table()` ou `unique()`

**Solução**

1.  Quantos veículos são do fabricante ‘Ford’ no total e somente para
    modelos ‘Sporty’?

**Solução**

1.  Qual o percentual de veículos são do fabricante ‘Ford’? E qual o
    percentual de veículos da Ford são ‘Sporty’?

**Solução**

1.  Qual o maior e o menor preço de veículos da ‘Ford’ ?

**Solução**

# Graficos_Ilum
Esse breve repósitório possui três funções que facilitam a minha vida fazendo gráficos no jupyter lab. 
Primeiramente temos que importar as bibliotecas:
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import lmfit
```
### importar():
A primeira função que vamos definir, permite importar uma coluna de dados do excel na forma de um dicionário, cuja chave é a primeira célula da coluna, que deve conter uma string, e o elemento correspondente a essa chave é uma lista dos valores da coluna.
### Exemplo:
Se tivermos dados de concentração, absorbância e as incertezas da absorbância podemos organizá-los na planilha:

![image](https://user-images.githubusercontent.com/106620307/177174524-f7338305-682b-4d88-8c41-32a86a131c71.png)

Com a função importar definida no graficos_ilum.ipynb podemos importar os dados para uma lista a partir do caminho do arquivo excel e do nome da coluna:
```
con = importar(r'C:\Users\marcos220057\Desktop\exemplo_dados.xlsx', 'con')
absor = importar(r'C:\Users\marcos220057\Desktop\exemplo_dados.xlsx', 'absor')
uabs = importar(r'C:\Users\marcos220057\Desktop\exemplo_dados.xlsx', 'uabs')
```
#### *atenção: o caminho desse exemplo é o do meu arquivo no meu computador, você deve escrever seu próprio caminho.

## plotar():
Agora podemos usar esses dados para testar a função plotar:
```
plotar(con, absor,uy = uabs, reta = True, legendas = ['Concentração [%]', 'Absrbância'], save = 'exemplo_grafico.png')
```
```
[[Model]]
    Model(reta)
[[Fit Statistics]]
    # fitting method   = leastsq
    # function evals   = 7
    # data points      = 11
    # variables        = 2
    chi-square         = 8.0061e-05
    reduced chi-square = 8.8956e-06
    Akaike info crit   = -126.136841
    Bayesian info crit = -125.341050
[[Variables]]
    a:  0.00125000 +/- 2.8438e-05 (2.28%) (init = 1)
    b:  0.03554545 +/- 0.00168239 (4.73%) (init = 1)
[[Correlations]] (unreported correlations are < 0.100)
    C(a, b) = -0.845
```
![image](https://user-images.githubusercontent.com/106620307/177175623-4e450bb2-3232-4fb7-9869-fb06304008a5.png)

A função retornou a imagem do gráfico, além dos parametros da reta:  a = 0.00125000 +/- 2.8438e-05   e  b = 0.03554545 +/- 0.00168239 junto com os parâmetros estatísticos da reta.

## histograma()
Por último, temos uma função que permite fazer histogramas de alguma medida.
### Exemplo:
Supondo que queremos ver a distribuição de notas de alguma matéria hipotética:
```
notas = importar(r'C:\Users\marcos220057\Desktop\exemplo 2.xlsx', 'notas')
histograma(notas, legendas = ['Nota', 'Frequência'], save = 'exemplo_histograma.png')
```
![image](https://user-images.githubusercontent.com/106620307/177180137-d075f562-a478-40ec-80c2-87e7eac2d4ca.png)

#### Para mais informações sobre cada função, faça:
```
print(importar.__doc__)
print(plotar.__doc__)
print(histograma.__doc__)
```

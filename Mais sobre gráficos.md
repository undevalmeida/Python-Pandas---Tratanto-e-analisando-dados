# Realizamos as importações padrão:
```
%matplotlib inline
import pandas as pd
import matplotlib.pyplot as plt
plt.rc('figure', figsize = (15,8))
```
#### Criaremos a área que sustentará o gráfico:
```
area = plt.figure() 
```
#### Iremos inserir quatro gráficos dentro desse área, começaremos adicionando:
```
g1 = area.add_subplot(2, 2, 1)
```
#### Isso quer dizer que dentro dessa figura há um gráfico, duas linhas e duas colunas na posição 1. Faremos o mesmo procedimento para o resto dos gráficos:
```
g1 = area.add_subplot(2, 2, 1)
g2 = area.add_subplot(2, 2, 2)
g3 = area.add_subplot(2, 2, 3)
g4 = area.add_subplot(2, 2, 4)
```
#### Começaremos produzindo um scatterplot, isto é, um gráfico de dispersão. Usaremos duas variáveis: Valor e Area.
```
g1.scatter(dados.Valor, dados.Area)
g1.set_title('Valor X Área')'
```
#### Criaremos o restante dos gráficos, e a cada um deles daremos um título diferente. No caso de g3, faremos uma amostra aleatória dentro do próprio dataframe. Neste caso, como já sabemos, o índice estará todo errado e fora de orndem. Para que possamos produzir um gráfico interessante, devemos refazer o índice ao escrever dados_g3.index = range(dados_g3.shape[0]) em nosso código
```
g1.scatter(dados.Valor, dados.Area)
g1.set_title('Valor X Área')

g2.hist(dados.Valor)
g2.set_title('Histograma')

dados_g3 = dados.Valor.sample(100) 
dados_g3.index = range(dados_g3.shape[0])
g3.plot(dados_g3)
g3.set_title('Amostra (Valor)')

grupo = dados.groupby('Tipo')['Valor']
label = grupo.mean().index
valores = grupo.mean().values
g4.bar(label, valores)
g4.set_title('Valor Médio por Tipo')
```

### Nos resta salvar esses conteúdos, e para fazer isso escreveremos:
```
area.savefig('grafico.png', dpi = 300, bbox_inches = 'tight')
```

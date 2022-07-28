# Car Price Prediction Multiple Linear Regression

Hi! Esse projeto foi feito para exemplificar a construção de modelos de regressão linear múltipla, para ter mais detalhes do seus desenvolvimento recomendo fortemente minha publicação no Medium sobre o assunto.
Medium: https://medium.com/@leandric/trabalhando-com-regress%C3%A3o-linear-40b780ebcf2
Kaggle: https://www.kaggle.com/datasets/hellbuoy/car-price-prediction


#  Declaração do problema

A empresa automobilística chinesa Geely Auto aspira entrar no mercado dos EUA estabelecendo sua unidade de fabricação lá e produzindo carros localmente para competir com seus colegas americanos e europeus.

Eles contrataram uma empresa de consultoria automobilística para entender os fatores dos quais depende o preço dos carros. Especificamente, eles querem entender os fatores que afetam os preços dos carros no mercado americano, pois podem ser muito diferentes do mercado chinês. A empresa quer saber:

Quais variáveis ​​são significativas na previsão do preço de um carro Como essas variáveis ​​descrevem o preço de um carro Com base em várias pesquisas de mercado, a empresa de consultoria reuniu um grande conjunto de dados de diferentes tipos de carros no mercado americano.

## Objetivo de Negócios

Somos obrigados a modelar o preço dos carros com as variáveis ​​independentes disponíveis. Ele será usado pela administração para entender exatamente como os preços variam com as variáveis ​​independentes. Eles podem manipular o design dos carros, a estratégia de negócios etc. para atender a determinados níveis de preços. Além disso, o modelo será uma boa maneira de a administração entender a dinâmica de preços de um novo mercado.

## Análise da Variável dependente (y)

![All your files and folders are presented as a tree in the file explorer. You can switch from one to another by clicking a file in the tree.](https://cdn-images-1.medium.com/max/800/1*qKqDy7NOPyP6NVZP0f2KqA.png)
![enter image description here](https://cdn-images-1.medium.com/max/800/1*sh1MsMGwMYMvb1nI4dTDzA.png)

O Preço dos automóveis possuem uma assimetria positiva o que pode causar uma maior dispersão entre os valores conforme se distanciam da média, portanto foi aplicado o logaritmo na variável com o objetivo de deixar mais próxima de uma distribuição normal.
![enter image description here](https://cdn-images-1.medium.com/max/800/1*KBRIaSFRlUiEyblULnVreg.png)

## Tratativas das Variáveis dependentes (x)


Foi aplicado a conversão das variáveis alfanuméricas com **LabelEncoder()** com objetivo de ter somente variáveis numéricas, com isso os números foram tratados para não ocorrer erros quando calcula-se o logaritmo.
Com os novos valores analisei quais variáveis possuem mais correlação com o **price**.

![enter image description here](https://cdn-images-1.medium.com/max/800/1*RzMWW5GMrqa5hNxxz3SOiA.png)
![enter image description here](https://cdn-images-1.medium.com/max/800/1*vyHHjG1MB3qFEs988qUuPg.png)
![enter image description here](https://cdn-images-1.medium.com/max/800/1*IVH7FzH7zInOERfq8sZCSQ.png)
![enter image description here](https://cdn-images-1.medium.com/max/800/1*JdNK5ijYbdy6ZeMnGEPI0Q.png)

Utilizando da função **.corr()** do dataframe pandas considerei as variáveis com correlação ≥0.3.

## Estimando qualidade das variaveis

![enter image description here](https://cdn-images-1.medium.com/max/800/1*0QjYv4PI2_RuwXIHnnTAJQ.png)

Após coletar o sumário estatistico considerei as variaveis com **P>|t|** inferior a 0.5.

## Resultado do Modeloenter code here
De posse das variáveis treinei um modelo considerado 80% da base sendo que os outros 20% foram separadas para teste.
Foi possível obter com o modelo um **R² de 0.873**, ou seja, para os dados no treinamento o modelo possui uma boa aderência.

![enter image description here](https://cdn-images-1.medium.com/max/800/1*YvTY_ETpRqL57RAWFNVdIg.png)

Agora considerando a base de teste obtive um **R² de 0.826**.
![enter image description here](https://cdn-images-1.medium.com/max/800/1*0e91tFbZ7qYsXcaBP8P_sA.png)
É possível notar o comportamento gerado devido assimetria positiva na variável **x(price)**.
## Conclusão para o problema
Por fim com esse estudo podemos concluir que as principais variáveis que para precificação de automóveis no mercado americano são:

-   **symboling** → Classificação De segurança de um automóvel.
-   **drivewheel** → Tipo de roda de acionamento.
-   **wheelbase** → Distância entre os eixos do automóvel
-   **carwidth** → Largura do automóvel.
-   **curbweight** → Peso do automóvel (sem ocupantes e bagagem)
-   **enginesize** →Tamanho do motor
-   **boreratio** → relação entre as dimensões do diâmetro do furo do cilindro do motor e o comprimento do curso do pistão.
-   **horsepower** → Cavalos de potência.

Com base nessas variáveis escolhidas por possuírem uma correlação alta com o preço conseguimos entrar um **R² de 0.826**, contudo é importante ressaltar que não obtivemos bons resultado com veículos mais caros (veículos de luxo), é que para esse tipo de veículo o que as variáveis podem ser relevantes para sua precificação podem ser diferentes, assim sendo necessário um novo estudo para esta classe de veículos.

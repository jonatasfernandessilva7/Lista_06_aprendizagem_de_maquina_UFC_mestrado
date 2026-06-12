# Trabalho Prático: Agrupamento com K-Médias e Redução de Dimensionalidade com PCA

Este repositório contém a resolução da **Lista 6** da disciplina de **Aprendizagem de Máquina (Período 2026.1)** do curso de Ciência da Computação da Universidade Federal do Ceará (UFC), ministrada pelo **Professor César Lincoln Cavalcante Mattos**.

O objetivo principal deste trabalho é consolidar os conceitos teóricos de aprendizagem não-supervisionada através da implementação nativa (*from scratch*) de dois dos algoritmos mais fundamentais da área: o **K-médias** (avaliando diferentes métricas de distância e critérios de validação de clusters) e a **Análise de Componentes Principais (PCA)** através da decomposição SVD.

---

## Estrutura do Projeto

O projeto está organizado da seguinte forma:
* `Lista_06_AMA.ipynb`: Jupyter Notebook contendo todo o código documentado, dividido em células prontas para execução, juntamente com as análises gráficas.
* `quake.csv`: Conjunto de dados composto por coordenadas geográficas (latitude e longitude) de locais onde foram registados sismos.
* `penguins.csv`: Conjunto de dados com medições anatómicas de três espécies de pinguins da Antártida.

---

## Descrição das Atividades

### Questão 1: K-médias e Índice Davies-Bouldin (DB)
Implementação do algoritmo K-médias a partir do zero, sem o uso de bibliotecas prontas para a modelação (`sklearn`). 
* **Item A (Distância Euclidiana):** O algoritmo corre em busca do hiperparâmetro $K$ ótimo no intervalo de $4$ a $20$. A escolha do melhor número de clusters é feita minimizando o **Índice Davies-Bouldin (DB)**. Para mitigar o problema dos mínimos locais da inicialização aleatória, são realizadas 20 repetições para cada $K$, selecionando a estrutura com menor erro de reconstrução.
* **Item B (Distância de Mahalanobis):** Adaptação completa do algoritmo K-médias e do cálculo do Índice DB para utilizar a distância de Mahalanobis, baseando-se na matriz de covariância inversa global dos dados.

### Questão 2: PCA (*Principal Component Analysis*) via SVD
Implementação nativa do algoritmo PCA recorrendo à função de Decomposição em Valores Singulares (`np.linalg.svd`) do NumPy para extração de autovetores e autovalores.
* **Item A (Projeção 2D):** Redução da dimensionalidade dos atributos do dataset `penguins.csv` de 4 para 2 dimensões. Visualização das amostras num gráfico de dispersão (*scatter plot*) colorido de acordo com as classes reais das espécies (*Adelie, Chinstrap, Gentoo*).
* **Item B (Variância Explicada):** Análise matemática e gráfica da Proporção de Variância Explicada Acumulada à medida que o número de componentes principais varia entre 1, 2, 3 e 4.

*Nota: Todos os dados de ambos os problemas são previamente normalizados utilizando a técnica de Z-score (padronização).*

---

## Tecnologias e Dependências

Os algoritmos foram codificados em **Python 3** utilizando apenas operações matriciais básicas. Foram utilizadas as seguintes bibliotecas auxiliares:
* **NumPy**: Para álgebra linear (operações com matrizes, inversão e o método SVD).
* **Pandas**: Apenas para a leitura e estruturação inicial dos ficheiros CSV.
* **Matplotlib** & **Seaborn**: Para a geração de gráficos de dispersão dos clusters, projeções e diagramas de variância.

---

## Como Executar no Google Colab

Este projeto foi desenhado para ser executado diretamente no ambiente cloud do Google Colab de forma simples:

1. Acesse o [Google Colab](https://colab.research.google.com/).
2. Crie um novo Notebook ou faça o upload do ficheiro `.ipynb` deste repositório.
3. No menu lateral esquerdo do Colab, clique no ícone de pasta (**Arquivos**) e faça o upload dos ficheiros de dados:
   * `quake.csv`
   * `penguins.csv`
4. Execute as células sequencialmente (`Shift + Enter`).

### Formato de Saída Esperado
* Gráfico de dispersão com os agrupamentos geográficos ótimos determinados pelo índice DB (tanto para a distância Euclidiana como para a de Mahalanobis).
* Gráfico bidimensional das componentes do PCA demonstrando o agrupamento natural das espécies de pinguins.
* Relatório textual e gráfico de barras exibindo a variância acumulada (onde 4 componentes devem totalizar 100% da informação).

---

## 📝 Diretrizes de Implementação da Disciplina
Conforme as instruções do docente:
* Os algoritmos não utilizam pacotes como `scikit-learn` para a lógica de clustering ou projeção.
* Os resultados e os gráficos gerados encontram-se totalmente visíveis diretamente nas células guardadas do notebook para facilitar a avaliação.

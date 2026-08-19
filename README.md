# Detecção de Logos Reais e Falsos com Inteligência Artificial

Este projeto tem como objetivo treinar um modelo de Inteligência Artificial capaz de classificar imagens de logos como **reais** ou **falsos** utilizando Python, Google Colab, TensorFlow/Keras e um dataset do Kaggle.

O projeto foi desenvolvido como parte de uma atividade acadêmica voltada ao treinamento de modelos de IA em ambiente Google Colab, com foco na documentação do processo, análise dos resultados e identificação das limitações do modelo.

---

## Objetivo do Projeto

O objetivo principal deste projeto é criar um modelo de classificação binária para analisar imagens de logos e classificá-las em duas categorias:

* **Real**: logos considerados reais/originais dentro do dataset.
* **Fake**: logos considerados falsos ou gerados dentro do dataset.

A proposta não é criar um verificador oficial de autenticidade de marcas, mas sim treinar um modelo capaz de aprender padrões visuais a partir de um conjunto de dados previamente rotulado.

---

## Dataset Utilizado

O dataset utilizado foi o **Fake/Real Logo Detection Dataset**, disponível no Kaggle.

Link do dataset:

```text
https://www.kaggle.com/datasets/prosperchuks/fakereal-logo-detection-dataset
```

Durante a análise da estrutura dos arquivos, foram identificadas duas pastas principais:

```text
genLogoOutput/
output/
```

Para o desenvolvimento do modelo, essas pastas foram reorganizadas da seguinte forma:

```text
dataset_final/
  fake/
  real/
```

A quantidade final de imagens ficou assim:

```text
fake: 550 imagens
real: 275 imagens
```

Isso mostra que o dataset é desbalanceado, pois possui mais exemplos da classe `fake` do que da classe `real`.

---

## Tecnologias Utilizadas

* Python
* Google Colab
* Kaggle API
* TensorFlow/Keras
* NumPy
* Matplotlib
* Scikit-learn
* Pandas

---

## Etapas do Projeto

### 1. Download do Dataset

O dataset foi baixado diretamente do Kaggle utilizando a API do Kaggle no Google Colab.

```python
!kaggle datasets download -d prosperchuks/fakereal-logo-detection-dataset
```

Depois, o arquivo foi descompactado:

```python
!unzip fakereal-logo-detection-dataset.zip -d logos_dataset
```

---

### 2. Organização dos Dados

As imagens foram reorganizadas em duas classes principais:

```text
fake
real
```

Essa organização facilitou o carregamento das imagens pelo TensorFlow.

---

### 3. Pré-processamento das Imagens

As imagens foram redimensionadas para:

```text
70x70 pixels
```

Esse tamanho foi utilizado para reduzir o custo computacional e facilitar o treinamento do modelo no Google Colab.

Também foi feita a separação automática dos dados em:

```text
80% para treinamento
20% para validação
```

---

### 4. Criação do Modelo

Foi criado um modelo de rede neural convolucional, também conhecido como **CNN**.

Esse tipo de modelo é bastante utilizado em problemas de visão computacional, pois consegue analisar padrões visuais em imagens, como formas, bordas, cores e estruturas.

A arquitetura utilizada foi composta por:

* Camada de normalização dos pixels.
* Camadas convolucionais.
* Camadas de pooling.
* Camada flatten.
* Camada densa.
* Camada de saída com ativação sigmoid.

A saída do modelo retorna uma classificação binária:

```text
real ou fake
```

---

## Treinamento

O modelo foi treinado por 10 épocas.

Resultado aproximado obtido:

```text
Acurácia de treinamento: 89%
Acurácia de validação: 90%
```

Esses resultados indicam que o modelo teve um bom desempenho geral dentro do conjunto de validação.

---

## Matriz de Confusão

A matriz de confusão mostrou que o modelo teve um desempenho melhor ao identificar logos falsos do que logos reais.

Resultado observado:

```text
121 logos fake classificados corretamente como fake.
0 logos fake classificados incorretamente como real.

28 logos reais classificados corretamente como real.
16 logos reais classificados incorretamente como fake.
```

Isso indica que o modelo aprendeu bem os padrões da classe `fake`, mas apresentou maior dificuldade com a classe `real`.

Uma possível explicação é o desbalanceamento do dataset, já que havia mais imagens falsas do que reais.

---

## Testes com Imagens Externas

Também foram feitos testes com imagens externas ao dataset.

Durante esses testes, foi observado que o modelo sempre tenta classificar a imagem como `real` ou `fake`, mesmo quando a imagem não pertence ao domínio esperado.

Isso acontece porque o modelo foi treinado apenas com duas classes. Ele não possui uma terceira categoria, como:

```text
não é logo
imagem inválida
não reconhecido
```

Portanto, uma limitação importante do modelo é que ele não deve ser usado como um verificador oficial de autenticidade de marcas.

---

## Limitações do Modelo

O modelo apresentou bons resultados no conjunto de validação, porém possui algumas limitações:

* O dataset é desbalanceado.
* As imagens possuem baixa resolução.
* O modelo só classifica imagens entre `real` e `fake`.
* O modelo não verifica se um logo é oficialmente verdadeiro ou falso.
* Imagens muito diferentes das imagens do dataset podem gerar previsões incorretas.
* O modelo não possui uma classe para imagens fora do domínio, como paisagens, pessoas ou objetos.

---

## Possíveis Melhorias Futuras

Algumas melhorias possíveis para versões futuras do projeto seriam:

* Usar um dataset maior.
* Equilibrar melhor a quantidade de imagens reais e falsas.
* Utilizar imagens com maior resolução.
* Criar uma terceira classe para imagens que não sejam logos.
* Testar modelos mais avançados de visão computacional.
* Aplicar técnicas de data augmentation.
* Usar transfer learning com modelos pré-treinados.

---

## Conclusão

O projeto conseguiu atingir seu objetivo principal: treinar um modelo de Inteligência Artificial capaz de classificar logos como reais ou falsos com base nos padrões aprendidos no dataset.

O modelo alcançou uma acurácia de validação próxima de 90%, o que representa um resultado satisfatório para uma primeira abordagem acadêmica.

Apesar disso, os testes também mostraram limitações importantes. O modelo não deve ser interpretado como uma ferramenta definitiva para validar autenticidade de marcas, mas sim como uma demonstração prática de classificação de imagens usando redes neurais convolucionais.

A análise dos erros e limitações torna o projeto mais completo, pois permite propor melhorias futuras e compreender melhor os desafios envolvidos no treinamento de modelos de IA.

---


## Status do Projeto

```text
Finalizado para fins acadêmicos...
```

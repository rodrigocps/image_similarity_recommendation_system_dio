# Sistema de Recomendação por Similaridade de Imagens

## Objetivo

O principal objetivo deste projeto é desenvolver um **Sistema de Recomendação Baseado em Conteúdo Visual** capaz de sugerir produtos que sejam visualmente semelhantes a um item de consulta.

Diferentemente dos sistemas tradicionais que dependem de metadados textuais (preço, marca, categoria), este modelo foca na aparência física dos produtos (cor, formato, textura), extraindo *features* visuais profundas e fornecendo recomendações baseadas exclusivamente na similaridade de imagem.

## Metodologia

O sistema é construído sobre os princípios da Transferência de Aprendizado (Transfer Learning) e Similaridade de Vetores, seguindo as seguintes etapas:

1.  **Transferência de Aprendizado (Extrator de Features):**
    * Utilizamos a rede neural **ResNet50**, pré-treinada no vasto *dataset* ImageNet, como base.
    * A camada de classificação final da ResNet50 é removida. A penúltima camada (após o *Global Average Pooling*) é usada para extrair um **vetor de *embedding*** de 2048 dimensões para cada imagem. Este vetor é a representação numérica e compacta da aparência visual do produto.

2.  **Vetorização do Catálogo:**
    * Todas as imagens do *dataset* de produtos (`Colors_Products.zip`) são processadas individualmente pelo extrator de *features*, criando um catálogo de *embeddings*.

3.  **Busca por Similaridade (KNN):**
    * O algoritmo **K-Vizinhos Mais Próximos (KNN)** é aplicado ao catálogo de *embeddings*.
    * Ao receber uma imagem de consulta, seu *embedding* é gerado, e a **Distância Cosseno** é utilizada para encontrar os $K$ vetores mais próximos no catálogo. Os produtos correspondentes são retornados como recomendações.

## Tecnologias Usadas

| Categoria | Tecnologia | Função no Projeto |
| :--- | :--- | :--- |
| **Ambiente de Execução** | Google Colab | Ambiente ideal para desenvolvimento de Deep Learning com acesso a GPU gratuita. |
| **Deep Learning** | TensorFlow / Keras | Criação, carregamento e manipulação do modelo CNN base. |
| **Modelo Base** | ResNet50 | Arquitetura CNN utilizada para **Transferência de Aprendizado** e extração de *features* visuais. |
| **Similaridade/Busca** | Scikit-learn (`NearestNeighbors`) | Implementação da técnica de **K-Vizinhos Mais Próximos (KNN)** para busca eficiente de similaridade. |
| **Manipulação de Dados** | Pandas, NumPy | Estruturação e gestão do catálogo de imagens/metadados e manipulação dos vetores de *embeddings*. |
| **Visualização** | Matplotlib | Exibição da imagem de consulta e das imagens recomendadas para validação do modelo. |

## Conjunto de Dados (Dataset)

O modelo foi treinado e validado utilizando um conjunto de dados de imagens de ressonância magnética cerebral.

* **Fonte:** [Brain Tumor Classification (MRI)](https://www.kaggle.com/datasets/sartajbhuvaji/brain-tumor-classification-mri/data)
* **Referência:** [Deep Learning with PyTorch Step-by-Step](https://github.com/dvgodoy/PyTorchStepByStep?tab=readme-ov-file)
* **Número de Imagens:** 3264 imagens 
* **Classes:** O dataset é composto por imagens categorizadas em quatro classes distintas:
    * `glioma_tumor`
    * `meningioma_tumor`
    * `no_tumor` (para casos sem tumor)
    * `pituitary_tumor`

## Resultados e Análises
Notebook com os parametros canal = 1 & n_feature = 32 (128x128): [LIDIA ADICIONAR O LINK]
Notebook com o Learning Rate: [LIDIA ADICIONAR O LINK]


## Resultados e Análises

As imagens foram submetidas a diversas etapas de pré-processamento para otimizar o treinamento do modelo, incluindo:


Dentre os parametros testados, os que ficaram no top 3 com os melhores resultados foram os em relação a Acurácia total de Validação	: 
para todos foram utilizados o msm  n_epochs = 20 


## canal = 3 & n_feature = 64 (64x64)
<img width="977" height="378" alt="32 3 64x64  loss" src="https://github.com/user-attachments/assets/a3c67371-abab-48e7-aa2e-1b78fe3f949d" />
<img width="901" height="760" alt="32 3 64x64 matriz" src="https://github.com/user-attachments/assets/464bca9f-00de-4e33-bdc0-037079395780" />


```
Acertos por classe (Acertos, Total):
- glioma_tumor: [24, 100]
- meningioma_tumor: [108, 115]
- no_tumor: [105, 105]
- pituitary_tumor: [64, 74]
```

```
Acurácia total de Validação: 301/394 (76.40%) 

Acurácia de Validação por Classe:
Classe 0: 24/100 (24.00%)
Classe 1: 108/115 (93.91%)
Classe 2: 105/105 (100.00%)
Classe 3: 64/74 (86.49%)
```

```
Acurácia total de Treinamento: 2843/2870 (99.06%)

Acurácia de Treinamento por Classe:
Classe 0: 819/826 (99.15%)
Classe 1: 807/822 (98.18%)
Classe 2: 391/395 (98.99%)
Classe 3: 826/827 (99.88%)
```




## canal = 3 & n_feature = 32 (64x64)
<img width="977" height="378" alt="64 3 64x64 loss" src="https://github.com/user-attachments/assets/eb38f573-2a6e-49a2-b373-64ee0cd722be" />
<img width="901" height="760" alt="64 3 64x64 matriz" src="https://github.com/user-attachments/assets/87e641fa-ccf2-4aa8-9674-4195dc90c9d6" />


```
Acertos por classe (Acertos, Total):
- glioma_tumor: [19, 100]
- meningioma_tumor: [113, 115]
- no_tumor: [105, 105]
- pituitary_tumor: [63, 74]
```

```
Acurácia total de Validação: 300/394 (76.14%)

Acurácia de Validação por Classe:
Classe 0: 19/100 (19.00%)
Classe 1: 113/115 (98.26%)
Classe 2: 105/105 (100.00%)
Classe 3: 63/74 (85.14%)
```

```
Acurácia total de Treinamento: 2863/2870 (99,76%) 

Acurácia de Treinamento por Classe:
Classe 0: 825/826 (99.88%)
Classe 1: 817/822 (99.39%)
Classe 2: 395/395 (100.00%)
Classe 3: 826/827 (99.88%)

```



## canal = 1 & n_feature = 32 (128x128) 
<img width="977" height="378" alt="32 1 128x128  loss" src="https://github.com/user-attachments/assets/5704728a-a70e-419d-a0a7-be811a5217a3" />
<img width="901" height="760" alt="32 1 128x128 matrzi" src="https://github.com/user-attachments/assets/f75d8c5e-6096-4c8a-ab89-e8383094b23f" />

```
Acertos por classe (Acertos, Total):
- glioma_tumor: [23, 100]
- meningioma_tumor: [105, 115]
- no_tumor: [105, 105]
- pituitary_tumor: [66, 74]
```

```
Acurácia total de Validação: 299/394 (75.89%)

Acurácia de Validação por Classe:
Classe 0: 23/100 (23.00%)
Classe 1: 105/115 (91.30%)
Classe 2: 105/105 (100.00%)
Classe 3: 66/74 (89.19%)
```


```
Acurácia total de Treinamento: 2845/2870 (99.13%)

Acurácia de Treinamento por Classe:
Classe 0: 824/826 (99.76%)
Classe 1: 801/822 (97.45%)
Classe 2: 394/395 (99.75%)
Classe 3: 826/827 (99.88%)
```



A segunda etapa do projeto foi realizada fazendo a aplicação do Learning Rate






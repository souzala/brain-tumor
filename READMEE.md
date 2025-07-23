## Conjunto de Dados (Dataset)

O modelo foi treinado e validado utilizando um conjunto de dados de imagens de ressonância magnética cerebral.

* **Fonte:** [Brain Tumor Classification (MRI)](https://www.kaggle.com/datasets/sartajbhuvaji/brain-tumor-classification-mri/data)
* **Classes:** O dataset é composto por imagens categorizadas em quatro classes distintas:
    * `glioma_tumor`
    * `meningioma_tumor`
    * `no_tumor` (para casos sem tumor)
    * `pituitary_tumor`
* **Número de Imagens:** 3264 imagens 

## Resultados e Análises

As imagens foram submetidas a diversas etapas de pré-processamento para otimizar o treinamento do modelo, incluindo:



O gráfico a seguir ilustra o comportamento das perdas de treinamento e validação com os seguintes parametros:

```
n_epochs = 16 # número de épocas 
seed = 42 # reprodutibilidade
```
<img width="977" height="378" alt="epocjs 16" src="https://github.com/user-attachments/assets/f34bb8f5-295d-4bb3-9418-013f06986fa4" />

Durante o treinamento, observou-se um problema estrutural de overfitting, onde, apesar do modelo continuar a aprender e a perda de treinamento diminuir, a perda de validação parou de diminuir ou começou a aumentar, indicando que o modelo estava memorizando os dados de treinamento em vez de generalizar para dados novos.

Nesse caso o overfitting parece ser um problema estrutural do treinamento, não apenas do número de épocas. Apesar do treinamento ter parado um pouco antes, o comportamento de divergência entre as perdas já estava presente.





 O numero de épocas foi alterado contudo ainda permaneceu um alto overfitting 

```
    n_epochs = 20 # número de épocas
    n_feature = 16 
```

 <img width="977" height="378" alt="ep 20" src="https://github.com/user-attachments/assets/49ccb445-b4e5-4d42-a384-2d35d0e6c3d5" /> <img width="541" height="456" alt="matriz 20" src="https://github.com/user-attachments/assets/d7527e2d-d4cd-4618-ae78-d20e2486e2d3" />




```
Acertos por classe (Acertos, Total):
- glioma_tumor: [15, 100]
- meningioma_tumor: [100, 115] 
- no_tumor: [98, 105]
- pituitary_tumor: [31, 74]
```

```
Acurácia total de Treinamento: 2696/2870 (93.94%)
```

```
Acurácia de Treinamento por Classe:
Classe 0: 798/826 (96.61%)
Classe 1: 706/822 (85.89%)
Classe 2: 375/395 (94.94%)
Classe 3: 817/827 (98.79%)
```

```
Acurácia total de Validação: 244/394 (61.93%)
```

```
Acurácia de Validação por Classe:
Classe 0: 15/100 (15.00%)
Classe 1: 100/115 (86.96%)
Classe 2: 98/105 (93.33%)
Classe 3: 31/74 (41.89%)
```

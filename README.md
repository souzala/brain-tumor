# 🧠 Brain Tumor Classification (MRI)

## 📌 Sobre o projeto
Este projeto tem como objetivo classificar imagens de ressonância magnética cerebral em quatro classes distintas de diagnóstico. Utilizamos redes neurais convolucionais (CNNs), com experimentações de diferentes configurações de canais, resolução e número de filtros (n_features), além da aplicação de técnicas como Hooks e Learning Rate para otimização do treinamento.


### 📂 Fonte do Dataset 
Utilizamos o dataset público disponível no Kaggle: [Brain Tumor Classification (MRI)](https://www.kaggle.com/datasets/sartajbhuvaji/brain-tumor-classification-mri/data)

### 📚 Referência Técnica
Nosso trabalho foi inspirado no repositório:
[Deep Learning with PyTorch Step-by-Step](https://github.com/dvgodoy/PyTorchStepByStep?tab=readme-ov-file)
Além dos notebooks desenvolvidos no componente de Aprendizado e Máquia: 

---

### 🧬 Estrutura do Dataset
O conjunto de dados é composto por **3.264 imagens de ressonância magnética (MRI)**, categorizadas nas seguintes classes:
    
- `glioma_tumor`
- `meningioma_tumor`
- `no_tumor` (sem tumor)
- `pituitary_tumor`

---

## 🧪 Metodologia e Experimentos
Realizamos experimentações variando **canal de entrada (grayscale ou RGB)**, **resolução da imagem** e **quantidade de filtros na primeira camada convolucional (n_feature)**.

As imagens passaram por etapas de **pré-processamento e normalização**, e o treinamento foi realizado por **20 épocas** em todos os testes.

📌 Notebooks utilizados
ADICONAR OS LINKSSS


## 📊 Resultados comparativos (CNN sem LR)
Abaixo estão os três principais experimentos que obtiveram melhores desempenhos em termos de acurácia de validação:



## 🔹 Experimento 1: `canal = 3`, `n_feature = 64`, `resolução = 64x64`

Acurácia de Validação por Classe
```
- glioma_tumor:      24/100 (24.00%)
- meningioma_tumor: 108/115 (93.91%)
- no_tumor:         105/105 (100.00%)
- pituitary_tumor:   64/74  (86.49%)
```
📌 Acurácia Total Validação: 76.40%

📌 Acurácia Total Treinamento: 99.06%

<img width="977" height="378" alt="32 3 64x64  loss" src="https://github.com/user-attachments/assets/a3c67371-abab-48e7-aa2e-1b78fe3f949d" />
<img width="901" height="760" alt="32 3 64x64 matriz" src="https://github.com/user-attachments/assets/464bca9f-00de-4e33-bdc0-037079395780" />




## 🔹 Experimento 2: canal = 3, n_feature = 32, resolução = 64x64

Acurácia de Validação por Classe
```
- glioma_tumor:      19/100 (19.00%)
- meningioma_tumor: 113/115 (98.26%)
- no_tumor:         105/105 (100.00%)
- pituitary_tumor:   63/74  (85.14%)
```
📌 Acurácia Total Validação: 76.14%

📌 Acurácia Total Treinamento: 99.76%

<img width="977" height="378" alt="64 3 64x64 loss" src="https://github.com/user-attachments/assets/eb38f573-2a6e-49a2-b373-64ee0cd722be" />
<img width="901" height="760" alt="64 3 64x64 matriz" src="https://github.com/user-attachments/assets/87e641fa-ccf2-4aa8-9674-4195dc90c9d6" />




## 🔹 Experimento 3: canal = 1, n_feature = 32, resolução = 128x128

Acurácia de Validação por Classe
```
- glioma_tumor:      23/100 (23.00%)
- meningioma_tumor: 105/115 (91.30%)
- no_tumor:         105/105 (100.00%)
- pituitary_tumor:   66/74  (89.19%)
```
📌 Acurácia Total Validação: 75.89%

📌 Acurácia Total Treinamento: 99.13%

<img width="977" height="378" alt="32 1 128x128  loss" src="https://github.com/user-attachments/assets/5704728a-a70e-419d-a0a7-be811a5217a3" />
<img width="901" height="760" alt="32 1 128x128 matrzi" src="https://github.com/user-attachments/assets/f75d8c5e-6096-4c8a-ab89-e8383094b23f" />



## 🚀 Otimização com Learning Rate 
Após os testes iniciais, passamos a investigar o impacto da escolha da **taxa de aprendizagem (Learning Rate)** utilizando a técnica de **StepLR** com diferentes combinações de `step_size` e `gamma`.

Testes realizados com:
- **Modelo base:** `1 canal`, `32 filtros`, `128x128`
- **Epochs:** 20
- **Variáveis de Scheduler:** `step_size` e `gamma`


### 🔬 Principais Resultados com LR

| Teste  | Step Size | Gamma | Validação (%) | Treinamento (%) | Melhor Classe      | Pior Classe       |
| ------ | --------- | ----- | ------------- | --------------- | ------------------ | ----------------- |
| **15** | 5         | 0.1   | **63.20%**    | 96.17%          | `no_tumor (97%)`   | `glioma (16%)`    |
| **17** | 5         | 0.5   | **71.57%**    | 99.30%          | `no_tumor (100%)`  | `glioma (19%)`    |
| **19** | 5         | 0.9   | **71.83%**    | 99.30%          | `meningioma (93%)` | `glioma (21%)`    |
| **21** | 3         | 0.9   | **72.84%**    | 99.13%          | `no_tumor (100%)`  | `glioma (22%)`    |
| **23** | 3         | 0.9   | **68.02%**    | 98.78%          | `meningioma (94%)` | `pituitary (47%)` |


### 🎯 Considerações dos testes
- O **melhor resultado geral** foi com o Teste 21 (`step_size = 3`, `gamma = 0.9`), com **72.84%** de acurácia na validação.
- A classe `glioma_tumor` foi consistentemente a mais desafiadora.
- Os testes mostraram que **escolhas cuidadosas de LR** podem ajudar a melhorar a generalização, mas que **a arquitetura da rede e o balanceamento de classes também são fatores decisivos**.



## 📈 Considerações Finais
- **Modelos com alta acurácia de treino** (>99%) não garantem bom desempenho em validação.
- O uso de **Learning Rate Scheduling (StepLR)** apresentou melhora em alguns casos, mas a **classe `glioma_tumor` permanece desafiadora**.
- O principal desafio observado foi a baixa acurácia na classe glioma_tumor, o que pode indicar dificuldade do modelo em generalizar para esse tipo de imagem.


---
### 👥 Autoras: 

- Larissa Soares de Souza 
- Lídia Gabrielly Dutra de Meneses Santos 






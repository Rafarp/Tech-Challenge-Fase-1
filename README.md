# Tech Challenge Fase 1 - Antecipação de NPS (E-commerce)
**Pós-Graduação em AI Scientist - FIAP**

## Objetivo do Projeto
O problema central abordado neste projeto é a reatividade de um e-commerce em relação à satisfação do consumidor, uma vez que o Net Promoter Score (NPS) atualmente é coletado apenas após o encerramento da jornada de compra. 

O objetivo é resolver a incapacidade da empresa de antecipar problemas, transformando dados operacionais (logística, pedidos e atendimento) em insights e modelos preditivos. Isso permitirá que a equipe de Customer Experience aja de forma preventiva e proativa para reverter atritos na experiência do cliente antes mesmo da aplicação da pesquisa.

## Descrição da Base de Dados
A análise foi construída sobre uma base de dados histórica contendo informações de pedidos, logística e suporte.
- **Formato:** Arquivo tabular (`.csv`)
- **Volume:** 2.500 registros e 19 atributos.
- **Principais Atributos:** 
  - **Perfil:** `customer_age`, `customer_region`, `customer_tenure_months`
  - **Logística:** `delivery_time_days`, `delivery_delay_days`, `freight_value`
  - **Atendimento:** `customer_service_contacts`, `resolution_time_days`, `complaints_count`
  - **Target (Alvo):** `nps_score` (Variando de 0 a 10).

## Metodologia Utilizada
O projeto foi dividido em duas grandes etapas:

1. **Análise Exploratória de Dados (EDA):** Focada em identificar as variáveis de maior correlação com a queda do NPS. Identificou-se que atrasos na entrega (`delivery_delay_days`) e fricção no atendimento são os maiores ofensores.
2. **Modelagem Preditiva (Classificação):** 
   - A nota contínua de NPS foi convertida em classes de negócio: Detrator (0-6), Neutro (7-8) e Promotor (9-10).
   - Aplicou-se exclusão de variáveis identificadoras (evitando ruídos) e da nota de CSAT interna (evitando *data leakage*).
   - Fez-se o tratamento de dados categóricos com *One-Hot Encoding* e a padronização de escalas com *StandardScaler*.
   - O algoritmo escolhido foi o **Random Forest Classifier** com pesos balanceados (`class_weight='balanced'`), devido à sua robustez com relações não lineares e pela explicabilidade (*Feature Importance*).
   - O modelo foi validado com foco na métrica de **Recall** para a classe "Detrator", visando minimizar os falsos negativos (não deixar clientes insatisfeitos passarem despercebidos).

## Como reproduzir os resultados
Siga os passos abaixo para rodar o projeto em sua máquina local ou no Google Colab:

1. Clone este repositório:
bash
git clone https://github.com/Rafarp/Tech-Challenge-Fase-1.git

2. Acesse a pasta do projeto:
cd Tech-Challenge-Fase-1

3. Certifique-se de ter o Python 3 instalado, junto com as bibliotecas principais:
pip install pandas numpy matplotlib seaborn scikit-learn

4. Navegue até a pasta notebooks/ e abra o arquivo
Tech_Challenge_Fase_1_Final_(1).ipynb utilizando o Google Colab.
Atenção: Não se esqueça de fazer o upload do arquivo desafio_nps_fase_1.csv (localizado na pasta data/) para o ambiente virtual antes de executar as células.

outro modo seria: 
1. Faça o download do arquivo Tech_Challenge_Fase_1_Final_(1).ipynb (na pasta notebooks) e da base de dados desafio_nps_fase_1.csv (na pasta data) deste repositório 
2. Acesse o [Google Colab](https://colab.research.google.com/) e faça o upload do arquivo Tech_Challenge_Fase_1_Final_(1).ipynb
3. No menu lateral esquerdo do Colab (ícone de pasta), faça o upload do arquivo desafio_nps_fase_1.csv para a raiz do ambiente virtual.
4. Execute as células do notebook sequencialmente (Shift + Enter) para visualizar o tratamento de dados, a análise exploratória e o modelo preditivo em ação.


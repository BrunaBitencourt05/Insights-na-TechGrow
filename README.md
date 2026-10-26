# 📉 Análise Exploratória e Previsão de Churn — SaaS

Repositório desenvolvido como parte de um projeto prático de ciência de dados e machine learning, focado na análise de cancelamento de clientes (*churn*) em uma empresa de modelo SaaS (Software as a Service). O objetivo principal foi realizar o pipeline completo de Análise Exploratória de Dados (EDA), tratamento/pré-processamento e treinamento de modelos preditivos para identificar quais clientes têm maior probabilidade de cancelar o serviço.

---

## 🚀 Etapas do Projeto

O projeto foi estruturado seguindo as melhores práticas de ciência de dados:

### 1. Inspeção Inicial e Verificação de Dados
* Importação e carregamento do dataset (`Caso_Pratico_base_churn_saas.csv`).
* Validação de integridade: verificação de valores nulos (`df.isnull().sum()`) e análise das estatísticas descritivas básicas (`df.describe()`).

### 2. Análise Exploratória de Dados (EDA)
* Construção de visualizações gráficas com **Seaborn** e **Matplotlib** para identificar padrões de comportamento dos clientes ativos vs. cancelados.
* Identificação do principal *insight* de negócio através do gráfico de **Boxplot**: a retenção é crítica no início da jornada, com a maior concentração de *churn* ocorrendo entre os **3 e 6 primeiros meses de contrato**.

### 3. Tratamento e Pré-processamento dos Dados
* **Remoção de Colunas Irrelevantes:** Exclusão da coluna de identificação `id_cliente` para evitar ruído e falsa correlação no modelo.
* **Encoding Categórico:** Aplicação de *One-Hot Encoding* (`pd.get_dummies`) em variáveis categóricas (como `plano` e `regiao`).
* **Padronização Numérica:** Escalonamento das variáveis numéricas (`tempo_contrato_meses`, `logins_mes`, `tickets_suporte`, `valor_mensal`, `qtd_funcionarios`, `uso_media_diaria_horas`) utilizando o `StandardScaler` do Scikit-Learn.
* **Matriz de Correlação:** Análise de mapa de calor (*heatmap*) para mapear a relação linear entre as variáveis tratadas e o *churn*.

### 4. Divisão e Treinamento de Modelos Preditivos
* Divisão dos dados em **70% para treino** e **30% para teste** com amostragem estratificada (`train_test_split`).
* Treinamento e comparação de três algoritmos de classificação:
  1. **Regressão Logística** (*Baseline*)
  2. **Random Forest Classifier**
  3. **XGBoost Classifier**

### 5. Avaliação e Comparação de Desempenho
* Avaliação de desempenho através de métricas de classificação (`Accuracy`, `Precision`, `Recall`, `F1-Score` e `ROC AUC Score`).
* Plotagem da **Curva ROC Comparativa** para medir a capacidade de discriminação dos modelos.
* Análise da **Importância das Variáveis** (*Feature Importance*) para mapear os principais direcionadores de cancelamento (`logins_mes`, `tickets_suporte`, `inadimplencia`, `uso_media_diaria

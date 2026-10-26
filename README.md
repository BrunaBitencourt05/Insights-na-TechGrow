📊 Previsão e Análise de Churn em SaaS

Repositório desenvolvido como parte de um projeto prático de Análise de Dados e Machine Learning, focado no entendimento e prevenção do cancelamento de clientes (churn) em uma empresa SaaS. O objetivo principal foi realizar o pipeline completo: desde a exploração inicial e tratamento dos dados até o treinamento e avaliação de modelos preditivos para apoiar decisões estratégicas do time de produto e Customer Success.

🚀 Etapas do Projeto

O projeto foi estruturado seguindo o ciclo de vida completo de Ciência de Dados:

1. Carregamento e Inspeção Inicial

Importação do dataset: Leitura do arquivo Caso_Pratico_base_churn_saas.csv utilizando Pandas.

Estatísticas Descritivas: Análise das métricas centrais e de dispersão (mean, std, quartis, min, max) com .describe().

Verificação de Valores Ausentes: Identificação e confirmação de integridade do dataset através de .isnull().sum() (0 valores nulos encontrados).

2. Análise Exploratória de Dados (EDA)

Distribuição da Variável Alvo (churn): Mapeamento do percentual de clientes ativos em relação aos cancelados.

Comportamento por Tempo de Contrato: Utilização de boxplots para identificar padrões. Foi constatado que a maioria dos cancelamentos ocorre precocemente (entre 3 e 6 meses de contrato).

Relação com Suporte e Valor Mensal: Análise do impacto de chamados abertos e preço na retenção dos usuários.

3. Tratamento e Pré-Processamento de Dados

Remoção de Colunas Redundantes: Exclusão da coluna de identificação id_cliente para evitar ruído e multicolinearidade na matriz de correlação.

Encoding de Variáveis Categóricas: Conversão de colunas textuais (plano, regiao) em formato numérico utilizando One-Hot Encoding (pd.get_dummies).

Padronização de Variáveis Numéricas: Aplicação do StandardScaler do Scikit-Learn em colunas como tempo_contrato_meses, logins_mes, tickets_suporte, valor_mensal, qtd_funcionarios e uso_media_diaria_horas.

Análise de Correlação: Geração de heatmap com Seaborn para avaliar interações entre as features.

4. Divisão e Treinamento de Modelos Machine Learning

Separação de Dados: Divisão do dataset na proporção de 70% para treino e 30% para teste, aplicando estratificação pela variável-alvo.

Treinamento Comparativo:

Baseline: Regressão Logística (Logistic Regression)

Ensemble Machine Learning: Random Forest Classifier

Gradient Boosting: XGBoost Classifier

5. Avaliação e Performance

Avaliação rigorosa do desempenho dos modelos no conjunto de teste utilizando as seguintes métricas de classificação:

Métricas: Accuracy, Precision, Recall, F1-Score e ROC AUC Score.

Visualizações: Plotagem da Matriz de Confusão e da Curva ROC Comparativa entre os três algoritmos.

💡 Principais Insights de Negócio & Recomendação

Janela Crítica de Cancelamento: O churn concentra-se fortemente nos primeiros meses de vida do cliente (entre o 3º e 6º mês).

Variáveis de Maior Impacto: Através da análise de importância de features do Random Forest, identificou-se que a quantidade de logins_mes, o volume de tickets_suporte e a inadimplencia são os indicadores mais relevantes para prever o cancelamento.

Ações Recomendadas para o Time de Produto/CS:

Onboarding Automatizado: Fortalecer a experiência inicial do usuário no 1º mês para acelerar a percepção de valor (Time to Value).

Alertas de Risco: Criar gatilhos para intervenção do time de Customer Success quando houver queda acentuada nos logins diários ou alta frequência de chamados no suporte.

🛠️ Tecnologias Utilizadas

Linguagem: Python

Ambiente: Google Colab / Jupyter Notebook

Manipulação de Dados: Pandas, NumPy

Visualização: Matplotlib, Seaborn

Machine Learning: Scikit-Learn, XGBoost

✒️ Autor

Desenvolvido por Bruno Bitencourt.

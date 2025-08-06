# 📊 Análise de Evasão de Clientes (Churn) - TelecomX II

Este projeto aprofunda a análise de dados de clientes de uma empresa de telecomunicações com o objetivo de identificar os principais fatores que contribuem para a evasão (churn). Através da aplicação de técnicas de Machine Learning, foram desenvolvidos e avaliados modelos preditivos capazes de antecipar quais clientes possuem maior probabilidade de cancelar seus serviços. Os insights gerados visam subsidiar a criação de estratégias de retenção proativas e altamente direcionadas, otimizando os esforços da empresa na manutenção de sua base de clientes.

## 📈 Requisitos

Para executar este projeto, são necessárias as seguintes bibliotecas Python:

- `pandas`: Para manipulação e análise de dados.
- `numpy`: Para operações numéricas de alto desempenho.
- `matplotlib`: Para criação de visualizações estáticas, interativas e animadas em Python.
- `seaborn`: Baseado em matplotlib, oferece uma interface de alto nível para desenhar gráficos estatísticos atraentes e informativos.
- `scikit-learn`: Para ferramentas de machine learning, incluindo pré-processamento, modelagem e avaliação.

> 📌 O projeto foi desenvolvido e executado no ambiente Google Colab, garantindo a facilidade de reprodução e acesso às bibliotecas necessárias.

## 📁 Estrutura do Projeto

O repositório contém o seguinte arquivo principal:

- `Telecom_X2_Melhorado.ipynb`: O notebook Jupyter principal, que abrange todas as etapas da análise, desde o carregamento dos dados até a avaliação dos modelos e interpretação dos resultados. Este notebook foi aprimorado com comentários detalhados, organização de código e cabeçalhos para melhor legibilidade e compreensão.

## 🔍 Objetivos

Os objetivos específicos deste projeto incluem:

- **Detectar os principais fatores que levam à saída dos clientes**: Através de análises exploratórias e da interpretabilidade dos modelos de Machine Learning, identificar as características dos clientes que estão mais correlacionadas com a decisão de evadir.
- **Construir modelos preditivos eficazes para prever a evasão**: Desenvolver e otimizar modelos de classificação que possam prever com alta acurácia e recall quais clientes estão em risco de churn.
- **Propor estratégias de retenção baseadas nos insights obtidos**: Traduzir os resultados da análise e da modelagem em recomendações acionáveis para a empresa, visando reduzir a taxa de evasão e aumentar a satisfação do cliente.

## ⚙️ Técnicas Utilizadas

### 📌 Pré-processamento de Dados

Esta etapa é crucial para preparar os dados para a modelagem, garantindo sua qualidade e formato adequado:

- **Remoção de colunas irrelevantes**: A coluna `Id_cliente` foi removida, pois não contribui para a previsão do churn e pode introduzir ruído no modelo.
- **One-hot encoding para variáveis categóricas**: Variáveis nominais como `Servico_internet`, `Contrato`, e `Metodo_pagamento` foram convertidas em representações numéricas binárias, permitindo que os modelos de Machine Learning as interpretem corretamente.
- **Normalização para modelos sensíveis à escala**: As features numéricas foram padronizadas usando `StandardScaler`, transformando-as para ter média zero e variância unitária. Isso é essencial para modelos como SVM e Regressão Logística, que são sensíveis à escala dos dados.
- **Tratamento de valores nulos**: Embora o dataset fornecido já estivesse pré-tratado, a pipeline de pré-processamento foi projetada para lidar com possíveis valores nulos, garantindo robustez.

### 📌 Análise Exploratória de Dados (EDA)

A EDA foi realizada para entender a distribuição dos dados, identificar padrões e relações entre as variáveis:

- **Proporção de churn**: Análise da distribuição da variável alvo (`Churn`) para entender o desbalanceamento das classes.
- **Correlação entre variáveis**: Utilização de mapas de calor (heatmaps) para visualizar a correlação entre as features, identificando variáveis altamente correlacionadas que poderiam indicar multicolinearidade ou redundância.
- **Boxplots para tempo de serviço e cobrança total vs. churn**: Gráficos de caixa foram empregados para comparar a distribuição de variáveis numéricas importantes (como `Tempo_servico` e `Cobranca_total`) em relação ao status de churn, revelando insights sobre o comportamento dos clientes que evadem.

### 📌 Modelagem Preditiva

Foram implementados e treinados três modelos de classificação para prever o churn:

- **Regressão Logística**: Um modelo linear simples e interpretável, frequentemente utilizado para problemas de classificação binária. É eficaz para identificar a direção e a magnitude da influência de cada feature na probabilidade de churn.
- **Random Forest**: Um algoritmo de ensemble baseado em árvores de decisão. Conhecido por sua robustez e capacidade de lidar com relações não-lineares e interações complexas entre as features, além de fornecer a importância das variáveis.
- **SVM (Support Vector Machine) com kernel linear**: Um modelo poderoso que busca encontrar o hiperplano que melhor separa as classes. A escolha do kernel linear permite a interpretação dos coeficientes, similar à Regressão Logística, para entender a contribuição de cada feature na fronteira de decisão.

### 📌 Avaliação de Modelos

A performance de cada modelo foi avaliada utilizando um conjunto abrangente de métricas:

- **Acurácia**: Proporção de previsões corretas sobre o total de previsões.
- **Precisão (Precision)**: Proporção de verdadeiros positivos entre todas as previsões positivas. Importante para minimizar falsos positivos (prever churn onde não há).
- **Recall (Revocação)**: Proporção de verdadeiros positivos entre todos os casos positivos reais. Crucial para problemas de churn, onde o objetivo é identificar o máximo de clientes que realmente evadirão (minimizar falsos negativos).
- **F1-score**: Média harmônica entre precisão e recall, oferecendo um equilíbrio entre as duas métricas.
- **Matriz de Confusão**: Tabela que sumariza o desempenho do modelo, mostrando os verdadeiros positivos, verdadeiros negativos, falsos positivos e falsos negativos.
- **Curva ROC (Receiver Operating Characteristic) e AUC (Area Under the Curve)**: Ferramentas gráficas que avaliam a capacidade do modelo de distinguir entre as classes. A AUC fornece uma medida agregada do desempenho do classificador em todos os possíveis limiares de classificação.
- **Curva de Precisão-Recall**: Especialmente útil para datasets desbalanceados, como é o caso da previsão de churn, onde a classe minoritária (churn) é de maior interesse.

## ✅ Principais Resultados

### 🔝 Variáveis com maior influência na evasão:

Através da análise dos coeficientes da Regressão Logística e da importância das features do Random Forest, as seguintes variáveis foram identificadas como as mais impactantes na decisão de churn:

- **Tempo de serviço (negativo)**: Clientes com menor tempo de serviço (novos clientes) tendem a ter uma probabilidade maior de evasão. Isso sugere que o período inicial de relacionamento com o cliente é crítico.
- **Cobrança total**: Clientes com cobranças totais mais baixas (que podem indicar menor uso de serviços ou planos mais básicos) ou com flutuações nas cobranças podem ter maior propensão a evadir.
- **Tipo de contrato**: Contratos mensais (`Month-to-month`) estão fortemente associados a uma maior taxa de churn, enquanto contratos de longo prazo (`One year`, `Two year`) indicam maior lealdade.
- **Tipo de internet (Fibra ótica)**: Curiosamente, clientes com serviço de internet por fibra ótica apresentaram uma tendência maior de churn, o que pode indicar problemas de qualidade, custo ou concorrência nesse segmento.
- **Forma de pagamento (cheque eletrônico)**: Clientes que utilizam cheque eletrônico como método de pagamento também demonstraram maior propensão à evasão, possivelmente devido à falta de automação ou conveniência em comparação com outros métodos.

### 🧠 Melhor Modelo:

Após a avaliação comparativa, a **Regressão Logística** destacou-se como o modelo mais adequado para este problema, especialmente considerando a interpretabilidade e o recall para a classe de interesse (churn):

- **Acurácia**: Aproximadamente **80.6%**
- **Recall (Evadiu)**: **53.6%** (o melhor entre os modelos testados, indicando uma boa capacidade de identificar clientes que realmente evadirão).
- **Alta interpretabilidade**: A natureza linear da Regressão Logística permite entender diretamente a contribuição de cada feature para a probabilidade de churn, facilitando a tomada de decisões estratégicas.

## 🎯 Estratégias Recomendadas de Retenção

Com base nos insights obtidos, as seguintes estratégias são recomendadas para a empresa de telecomunicações:

- **Incentivar contratos mais longos**: Oferecer descontos ou benefícios exclusivos para clientes que optarem por contratos anuais ou bienais, reduzindo a flexibilidade de saída e aumentando a lealdade.
- **Promover pagamento automático por cartão**: Incentivar a adesão a métodos de pagamento mais convenientes e automatizados, como débito automático em cartão de crédito, para reduzir o atrito e a probabilidade de churn associada a métodos manuais.
- **Acompanhar de perto novos clientes (0–6 meses)**: Implementar programas de onboarding e acompanhamento proativo para clientes nos primeiros meses de serviço, oferecendo suporte personalizado e garantindo uma experiência positiva para reduzir a evasão precoce.
- **Analisar e melhorar a experiência com internet por fibra**: Investigar as razões por trás do churn de clientes com fibra ótica. Isso pode envolver melhorias na qualidade do serviço, suporte técnico especializado ou ofertas mais competitivas para reter esses clientes.
- **Oferecer upgrade ou personalização para clientes com baixa cobrança total**: Identificar clientes com menor gasto mensal e propor pacotes de serviços personalizados ou upgrades que agreguem valor, incentivando o uso e a permanência.

## 🚀 Próximos Passos e Melhorias Sugeridas

Para aprimorar ainda mais este projeto e a capacidade preditiva, sugere-se os seguintes próximos passos:

- **Engenharia de Features Avançada**: Explorar a criação de novas features a partir das existentes, como a taxa de variação da cobrança mensal, ou a criação de segmentos de clientes baseados em seu perfil de uso.
- **Exploração de Outros Modelos**: Testar outros algoritmos de Machine Learning, como Gradient Boosting (XGBoost, LightGBM) ou redes neurais, que podem capturar padrões mais complexos nos dados.
- **Otimização de Hiperparâmetros**: Utilizar técnicas como GridSearchCV ou RandomizedSearchCV para otimizar os hiperparâmetros dos modelos, buscando maximizar o desempenho (especialmente o recall).
- **Tratamento de Desbalanceamento de Classes**: Implementar técnicas mais avançadas para lidar com o desbalanceamento da classe de churn, como SMOTE (Synthetic Minority Over-sampling Technique) ou ajuste de pesos de classe nos modelos.
- **Implantação do Modelo (Deployment)**: Desenvolver uma API simples para que o modelo possa ser integrado a sistemas de produção, permitindo previsões em tempo real.
- **Monitoramento Contínuo**: Estabelecer um processo de monitoramento da performance do modelo em produção, garantindo que ele continue relevante e preciso ao longo do tempo, e retreiná-lo periodicamente com novos dados.
- **Análise de Custo-Benefício**: Realizar uma análise aprofundada do custo-benefício das estratégias de retenção propostas, quantificando o impacto financeiro da redução do churn.


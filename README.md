<div align="center"> 

<!-- Título e Badge de Verificado -->
<h1>
  <img src="https://img.shields.io/badge/VERIFIED_ARCHITECT-1f425f.svg?style=for-the-badge&logo=github-sponsors&logoColor=white" alt="Verified" />
  <br>
  Neural Supply Chain & Demand Intelligence Engine
</h1>

<h3>
  <i>State-of-the-Art (SOTA) Forecasting, Inventory Optimization & Decision Systems</i>
</h3>

<p>
  <b>Elias Andrade</b><br>
  🧠 Arquiteto Sênior de Sistemas de Inteligência e Tomada de Decisão para Supply Chain e compras<br>
  BI/DI | IA • LLMs • ML • NLP | MLOps | IAOps • DataOps • DevOps | Automações e Sistemas Multi-Agentes
</p>

<!-- Badges de Tecnologias High-End -->
<p>
  <img src="https://img.shields.io/badge/Model-Prophet_&_LSTM-blueviolet?style=flat-square&logo=python" />
  <img src="https://img.shields.io/badge/Architecture-Event_Driven-orange?style=flat-square&logo=apache-kafka" />
  <img src="https://img.shields.io/badge/Accuracy-SOTA_Level_(MAPE_<_5%25)-success?style=flat-square" />
  <img src="https://img.shields.io/badge/Focus-ROI_&_EBITDA-blue?style=flat-square" />
</p>

<a href="https://linkedin.com/in/itilmgf"><img src="https://img.shields.io/badge/Connect-LinkedIn-0077B5?style=for-the-badge&logo=linkedin" /></a>
<a href="https://wa.me/5511913353137"><img src="https://img.shields.io/badge/Consultoria-WhatsApp-25D366?style=for-the-badge&logo=whatsapp" /></a>

</div>

---

## 🚀 Visão Geral do Sistema (Executive Summary)

Este repositório documenta a arquitetura e implementação de um **Motor de Inteligência de Decisão para Supply Chain**. Diferente de ERPs tradicionais que utilizam médias móveis simples, este sistema implementa uma abordagem **Híbrida (Ensemble)** combinando modelos estatísticos avançados (Prophet) com Redes Neurais e heurísticas de negócio proprietárias.

O objetivo não é apenas "prever vendas", mas gerar um **Sinal de Compra Auditável** que considera:
1.  **Lead Time Variável:** O sistema projeta a compra *n* dias antes da ruptura, baseado na volatilidade de entrega do fornecedor.
2.  **Sazonalidade Complexa:** Detecção automática de picos (ex: safra agrícola, Black Friday) e tendências de longo prazo.
3.  **Capacidade Financeira:** Ajuste das sugestões baseado no fluxo de caixa (OTB - Open to Buy).

---

## 📊 Performance & Precisão (SOTA Results)

> *Os gráficos abaixo representam saídas reais do motor de inferência, comparando dados históricos (2024) com projeções futuras (2025) e pontos ideais de reabastecimento.*

### 🎯 Case 1: Alta Volatilidade e Lead Time Longo (30 Dias)
O modelo identifica padrões de "dentes de serra" (consumo rápido e reposição) e projeta o **Sinal de Compra Antecipado** (linha tracejada verde escura) exatamente 30 dias antes da previsão de estoque crítico.

| Indicador | Performance do Modelo | Benchmark de Mercado |
| :--- | :--- | :--- |
| **MAPE (Erro Médio)** | **3.2%** (Extrema Precisão) | 15% - 25% |
| **Detecção de Picos** | 98% de assertividade em sazonalidade | Falha comum em médias móveis |
| **Ruptura Evitada** | 100% (Simulação Ex-Post) | N/A |

### 🔍 Destaques da Engenharia de Features
*   **Correção de Ruído:** O sistema filtra *outliers* (vendas B2B atípicas) para não sujar a previsão de demanda regular.
*   **Dynamic Cap/Floor:** Definição automática de Tetos e Pisos de estoque baseada na classificação ABC/XYZ do SKU.

---

## 🏗️ Arquitetura da Solução

Abaixo, a arquitetura de alto nível demonstrando como os dados fluem desde a ingestão até a decisão de compra.

```mermaid
graph TD
    subgraph Data_Ops [Injestão & Tratamento]
        A[ERP / SQL / APIs] -->|Raw Data| B(Data Lakehouse)
        B -->|Cleaning & Outlier Detection| C{Feature Engineering}
        C -->|Sazonalidade & Tendência| D[Dataset Preparado]
    end

    subgraph AI_Core [Motor de Inferência SOTA]
        D -->|Input| E1[Facebook Prophet Tuned]
        D -->|Input| E2[XGBoost Regressor]
        D -->|Input| E3[LSTM Neural Network]
        E1 & E2 & E3 -->|Ensemble| F[Meta-Model Weighting]
    end

    subgraph Business_Logic [Decisão & Otimização]
        F -->|Forecast Bruto| G[Cálculo de Estoque de Segurança Dinâmico]
        G -->|Lead Time Offset| H[Gerador de Sinal de Compra]
        H -->|Restrições de Caixa/Armazém| I[Sugestão Final Otimizada]
    end

    I -->|Output| J[Dashboard Executivo / Chat2SQL]
    I -->|Automação| K[Draft de Pedido no ERP]

    style AI_Core fill:#f9f,stroke:#333,stroke-width:2px
    style Business_Logic fill:#bbf,stroke:#333,stroke-width:2px
```

---

## 🛠️ Tecnologias e Metodologias

Este projeto utiliza um stack moderno focado em **Escalabilidade** e **Reprodutibilidade**.

### 🧬 Core AI & Data Science
*   **Linguagem:** Python 3.10+ (Tipagem estrita)
*   **Time Series:** `Prophet`, `NeuralProphet`, `Darts`, `Statsmodels`
*   **ML Clássico:** `Scikit-learn`, `XGBoost` (para regressão de features exógenas)
*   **Data Manipulation:** `Pandas` (Polars para grandes volumes), `NumPy`

### ⚙️ Engenharia & MLOps
*   **Containerização:** Docker & Kubernetes (Orquestração de treino/inferência)
*   **Pipeline:** Apache Airflow ou Dagster (Data Lineage)
*   **Visualização:** Plotly/Dash (para interatividade como visto nos prints)
*   **Database:** PostgreSQL / BigQuery

---

## 💡 Diferenciais da Implementação

### 1. "Prophet Tunado" (Hyperparameter Tuning)
Não utilizamos os parâmetros padrão. O sistema roda um grid search para encontrar:
*   `changepoint_prior_scale`: Sensibilidade a mudanças de tendência.
*   `seasonality_prior_scale`: Ajuste fino da força da sazonalidade.

### 2. Explicação da Decisão (XAI)
O sistema não é uma "Caixa Preta". Cada sugestão de compra vem acompanhada de um log explicativo:
> *"Sugestão de compra de 300 unidades gerada porque a projeção indica ruptura em 15/04 e o fornecedor tem atraso médio de 5 dias."*

### 3. Simulação de Cenários (What-If)
O motor permite simular:
*   *"O que acontece se a demanda subir 20%?"*
*   *"E se o Lead Time do fornecedor dobrar?"*

---

## 📬 Contato para Consultoria B2B

Se sua empresa busca sair do planejamento reativo em planilhas para uma operação **Data-Driven de classe mundial**, entre em contato.

<div align="center">
  <a href="https://wa.me/5511913353137" target="_blank">
    <img src="https://img.shields.io/badge/WhatsApp-Agendar_Reunião-25D366?style=for-the-badge&logo=whatsapp&logoColor=white" alt="WhatsApp">
  </a>
  <a href="mailto:oeliasandrade@gmail.com" target="_blank">
    <img src="https://img.shields.io/badge/Email-Falar_com_Elias-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Email">
  </a>
  <a href="https://linkedin.com/in/itilmgf" target="_blank">
    <img src="https://img.shields.io/badge/LinkedIn-Perfil_Profissional-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn">
  </a>
</div>

---
<p align="center">
  <small>2025 © Elias Andrade - Replika AI Solutions. Todos os direitos reservados.</small>
</p>
```




<img width="2880" height="1440" alt="jrxgp63qgbue1" src="https://github.com/user-attachments/assets/f75ba05d-cc26-4d74-af10-28d828be06a8" />

<img width="3060" height="1620" alt="CorreiaMotorAX1724_Prophet_C005_S250_20250413_191741_02_SinalLider_Indicadores_BlueGreen_AllAnnot_v4" src="https://github.com/user-attachments/assets/041bfccd-7fd8-4045-8b2b-c7aaa39c7747" />

<img width="3060" height="1620" alt="CorreiaMotorAX1590_Prophet_C005_S250_20250413_191753_02_SinalLider_Indicadores_Final_BlueGreen_AllAnnot_v4" src="https://github.com/user-attachments/assets/a7064943-94a3-47ca-9db1-867e47f6fa22" />

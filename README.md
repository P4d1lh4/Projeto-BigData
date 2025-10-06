# 🎬 Pipeline de Big Data: Análise de Produção Cinematográfica

## 📋 Descrição do Projeto

Este projeto implementa um pipeline completo de Big Data para análise da indústria cinematográfica, abrangendo desde a coleta de dados até a geração de insights visuais. O objetivo é identificar padrões de produção, receita e popularidade de filmes, auxiliando produtoras e investidores em decisões estratégicas.

**Disciplina**: Fundamentos de Big Data  
**Instituição**: CESAR School
**Período**: 2025.2

## 👥 Equipe

- Arthur Padilha
- Eduarda Souza
- Victor Melo

## 🎯 Problema de Negócio

**Desafio**: Compreender quais fatores influenciam o sucesso comercial e crítico dos filmes na indústria cinematográfica.

**Solução**: Pipeline de dados que processa e analisa informações de milhares de filmes para identificar:
- Gêneros mais lucrativos
- Relação entre orçamento e receita (ROI)
- Tendências temporais de produção
- Fatores de sucesso na indústria

## 📊 Fontes de Dados

### 1. movies_metadata.csv
- **Descrição**: Metadados detalhados sobre filmes
- **Origem**: The Movie Database (TMDb)
- **Tipo**: Dados estruturados
- **Campos principais**: título, orçamento, receita, gêneros, idioma, data de lançamento, popularidade, avaliação

### 2. credits.csv
- **Descrição**: Informações sobre elenco e equipe de produção
- **Origem**: The Movie Database (TMDb)
- **Tipo**: Dados semi-estruturados (JSON dentro de CSV)
- **Campos principais**: cast (elenco), crew (equipe técnica), id do filme

## 🏗️ Arquitetura do Pipeline

O projeto implementa todas as 5 etapas obrigatórias de um pipeline de Big Data:

### 1️⃣ Fontes de Dados (Data Sources)
- Dois datasets CSV com dados da indústria cinematográfica
- Dados estruturados e semi-estruturados

### 2️⃣ Ingestão (Ingestion)
- **Método**: Batch (lotes)
- **Ferramenta**: Pandas (`read_csv`)
- **Volume**: ~45.000 filmes e créditos

### 3️⃣ Transformação (Transformation)
- Limpeza de dados (remoção de nulos, tratamento de inconsistências)
- Normalização de campos numéricos e datas
- Enriquecimento (criação de colunas derivadas: ROI, lucro, categorias)
- Processamento de dados JSON (extração de gêneros, elenco, diretores)
- Integração de datasets (merge por ID)

### 4️⃣ Carregamento (Loading)
- **Arquitetura Medalhão**:
  - **Bronze**: Dados brutos (CSV original)
  - **Silver**: Dados limpos e normalizados
  - **Gold**: Dados prontos para análise
- **Formatos**: CSV e Parquet
- **Localização**: `/dados/bronze`, `/dados/silver`, `/dados/gold`

### 5️⃣ Destino (Destination)
- Visualizações interativas (Matplotlib, Seaborn)
- Dashboard analítico no Jupyter Notebook
- Insights de negócio para tomada de decisão

## 🛠️ Tecnologias Utilizadas

### Linguagem
- Python 3.8+

### Bibliotecas Principais
- **Manipulação de Dados**: `pandas`, `numpy`
- **Visualização**: `matplotlib`, `seaborn`
- **Armazenamento**: `pyarrow` (Parquet)
- **Processamento**: `json`

### Ferramentas
- Jupyter Notebook
- Git/GitHub

## 📁 Estrutura de Diretórios

```
BigData/
├── README.md
├── credits.csv
├── movies_metadata.csv
├── dados/
│   ├── bronze/          # Dados brutos
│   ├── silver/          # Dados limpos
│   └── gold/            # Dados para análise
├── codigo/
│   └── pipeline_big_data_filmes.ipynb
└── documentacao/
    ├── arquitetura.md
    └── checklist_av1.md
```

## 🚀 Como Executar

### Pré-requisitos
```bash
pip install pandas numpy matplotlib seaborn pyarrow
```

### Execução
1. Clone o repositório:
```bash
git clone [URL_DO_REPOSITORIO]
cd BigData
```

2. Abra o Jupyter Notebook:
```bash
jupyter notebook codigo/pipeline_big_data_filmes.ipynb
```

3. Execute todas as células sequencialmente (Cell > Run All)

## 📈 Principais Insights

### 🎭 Gêneros Mais Lucrativos
- Identificação dos top 10 gêneros por receita total
- Análise de rentabilidade por categoria

### 📅 Evolução Temporal
- Crescimento da produção cinematográfica entre 1980-2020
- Identificação de picos de produção

### 💰 ROI (Return on Investment)
- Relação entre orçamento e receita
- Identificação de filmes com melhor retorno sobre investimento
- Análise de break-even point

### 💼 Distribuição de Orçamento
- Categorização de filmes por faixa de investimento
- Análise percentual de distribuição

## 📚 Documentação Adicional

- **Arquitetura Detalhada**: Ver `documentacao/arquitetura.md`
- **Checklist AV1**: Ver `documentacao/checklist_av1.md`

## 🔄 Próximos Passos (Roadmap)

- [ ] Implementar processamento de streaming (simulação)
- [ ] Adicionar mais fontes de dados (APIs do TMDb, Twitter)
- [ ] Implementar machine learning para predição de sucesso
- [ ] Criar dashboard interativo com Plotly/Dash
- [ ] Deploy em cloud (AWS/GCP/Azure)

## 📝 Licença

Este projeto é desenvolvido para fins acadêmicos.

## 📧 Contato

Para dúvidas ou sugestões, entre em contato com a equipe através do repositório GitHub.

---

**Última atualização**: Outubro 2025


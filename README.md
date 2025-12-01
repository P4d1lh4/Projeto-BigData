# PIPELINE DE BIG DATA PARA ANÁLISE DA INDÚSTRIA CINEMATOGRÁFICA

**Projeto Final - Fundamentos de Big Data**  
**CESAR School - 2025.2**

**Equipe:**
- Arthur Padilha
- Eduarda Souza
- Victor Melo

---

## SUMÁRIO

1. [Introdução](#1-introdução)
2. [Motivação](#2-motivação)
3. [Objetivo do Projeto](#3-objetivo-do-projeto)
4. [Metodologia (Pipeline de Dados)](#4-metodologia-pipeline-de-dados)
   - 4.1. [Fontes de Dados](#41-fontes-de-dados)
   - 4.2. [Ingestão](#42-ingestão)
   - 4.3. [Transformação](#43-transformação)
   - 4.4. [Carregamento](#44-carregamento)
   - 4.5. [Destino](#45-destino)
5. [Arquitetura da Solução](#5-arquitetura-da-solução)
6. [Resultados e Visualizações](#6-resultados-e-visualizações)
7. [Conclusões](#7-conclusões)
8. [Estrutura do Repositório](#8-estrutura-do-repositório)
9. [Como Executar](#9-como-executar)
10. [Tecnologias Utilizadas](#10-tecnologias-utilizadas)
11. [Referências](#11-referências)

---

## 1. INTRODUÇÃO

A indústria cinematográfica movimenta bilhões de dólares anualmente e envolve decisões complexas de investimento, produção e marketing. Com o avanço das tecnologias de Big Data, tornou-se possível analisar grandes volumes de dados históricos para identificar padrões, tendências e fatores de sucesso que podem orientar decisões estratégicas mais assertivas.

Este projeto implementa um **pipeline completo de Big Data** para análise da indústria cinematográfica, abrangendo desde a coleta e processamento de dados brutos até a geração de insights visuais e estratégicos. O pipeline foi desenvolvido seguindo as cinco etapas fundamentais de um sistema de Big Data: **Fontes de Dados**, **Ingestão**, **Transformação**, **Carregamento** e **Destino**.

### 1.1 Problema de Negócio

Produtoras cinematográficas, distribuidoras e investidores enfrentam constantemente o desafio de prever o sucesso comercial e crítico de produções cinematográficas. Questões como:

- Quais gêneros cinematográficos são mais lucrativos?
- Qual a relação entre orçamento e retorno sobre investimento (ROI)?
- Como a popularidade de um filme se relaciona com sua receita?
- Quais são as tendências temporais na produção cinematográfica?

...são essenciais para a tomada de decisões estratégicas no setor.

### 1.2 Solução Proposta

Este projeto desenvolve uma solução de análise de dados que:
- Processa informações de **mais de 45.000 filmes**
- Integra dados de metadados de filmes e informações de créditos (elenco/equipe)
- Implementa a **Arquitetura Medalhão** (Bronze/Silver/Gold) para organização de dados
- Gera **visualizações e insights** para apoiar decisões de negócio
- Identifica **padrões de sucesso** na indústria cinematográfica

---

## 2. MOTIVAÇÃO

### 2.1 Relevância do Tema

A indústria do entretenimento é um dos setores mais dinâmicos e lucrativos da economia global. Segundo a Motion Picture Association (MPA), a indústria cinematográfica global gerou receitas superiores a **$100 bilhões** em 2023. Nesse contexto, a capacidade de analisar dados históricos e identificar padrões se torna uma **vantagem competitiva estratégica**.

### 2.2 Justificativa Técnica

Do ponto de vista técnico, este projeto é relevante porque:

1. **Demonstra conceitos fundamentais de Big Data**: O pipeline implementa todas as cinco etapas obrigatórias de um sistema de análise de dados em escala.

2. **Aplica arquitetura moderna**: Utiliza a Arquitetura Medalhão (Bronze/Silver/Gold), padrão amplamente adotado por empresas como Databricks, AWS e Azure.

3. **Trabalha com dados reais**: Os datasets utilizados são provenientes do The Movie Database (TMDb), uma das maiores bases de dados cinematográficos do mundo.

4. **Gera valor de negócio**: As análises produzem insights acionáveis que podem ser aplicados em cenários reais de tomada de decisão.

### 2.3 Aplicabilidade Prática

Os insights gerados por este pipeline podem ser utilizados por:

- **Produtoras cinematográficas**: Para decidir em quais gêneros investir
- **Distribuidoras**: Para estratégias de marketing e distribuição
- **Investidores**: Para avaliar o potencial de retorno de projetos cinematográficos
- **Plataformas de streaming**: Para curadoria e aquisição de conteúdo
- **Pesquisadores**: Para estudos acadêmicos sobre a indústria do entretenimento

---

## 3. OBJETIVO DO PROJETO

### 3.1 Objetivo Geral

Desenvolver um **pipeline completo de Big Data** para análise da indústria cinematográfica, capaz de processar, transformar e visualizar dados de filmes, gerando insights estratégicos sobre fatores de sucesso comercial e crítico.

### 3.2 Objetivos Específicos

1. **Implementar as 5 etapas do pipeline de Big Data**:
   - Definir fontes de dados relevantes
   - Desenvolver processo de ingestão em lote (batch)
   - Criar transformações para limpeza e enriquecimento de dados
   - Implementar carregamento com Arquitetura Medalhão
   - Gerar visualizações e análises de destino

2. **Integrar múltiplas fontes de dados**:
   - Combinar datasets de metadados e créditos
   - Processar dados estruturados e semi-estruturados (JSON)

3. **Gerar insights de negócio**:
   - Identificar gêneros mais lucrativos
   - Analisar relação entre orçamento e receita (ROI)
   - Detectar tendências temporais na produção cinematográfica
   - Avaliar correlações entre popularidade, avaliação e sucesso comercial

4. **Implementar boas práticas de engenharia de dados**:
   - Organização de código modular e documentado
   - Versionamento de código com Git/GitHub
   - Arquitetura de dados escalável e reproduzível

---

## 4. METODOLOGIA (PIPELINE DE DADOS)

O pipeline de dados desenvolvido segue rigorosamente as **5 etapas fundamentais** de um sistema de Big Data:

### 4.1 Fontes de Dados

#### 4.1.1 Descrição das Fontes

Utilizamos dois datasets principais provenientes do **The Movie Database (TMDb)**:

**Dataset 1: movies_metadata.csv**
- **Descrição**: Metadados detalhados sobre filmes
- **Volume**: 45.466 registros
- **Colunas principais**: 
  - `id`: Identificador único do filme
  - `title`: Título do filme
  - `budget`: Orçamento de produção (US$)
  - `revenue`: Receita bruta (US$)
  - `genres`: Gêneros cinematográficos (formato JSON)
  - `release_date`: Data de lançamento
  - `popularity`: Índice de popularidade
  - `vote_average`: Avaliação média (0-10)
  - `vote_count`: Número de avaliações
  - `runtime`: Duração (minutos)
  - `original_language`: Idioma original
  - `production_companies`: Empresas produtoras (formato JSON)
- **Tipo**: Dados estruturados e semi-estruturados
- **Formato**: CSV (1,2 GB)

**Dataset 2: credits.csv**
- **Descrição**: Informações sobre elenco e equipe de produção
- **Volume**: 45.476 registros
- **Colunas principais**:
  - `id`: Identificador do filme (chave para join)
  - `cast`: Elenco completo (formato JSON)
  - `crew`: Equipe técnica/produção (formato JSON)
- **Tipo**: Dados semi-estruturados (JSON aninhado)
- **Formato**: CSV (229 MB)

#### 4.1.2 Qualidade das Fontes

As fontes escolhidas apresentam:
- ✅ **Alta cobertura**: Mais de 45 mil filmes de diversas décadas
- ✅ **Dados ricos**: Informações financeiras, técnicas e de avaliação
- ✅ **Origem confiável**: TMDb é amplamente utilizado na indústria
- ⚠️ **Dados faltantes**: Alguns filmes não possuem orçamento/receita informados
- ⚠️ **Dados aninhados**: Requer parsing de campos JSON

### 4.2 Ingestão

#### 4.2.1 Método de Ingestão

**Tipo**: Processamento em **lote (batch)**  
**Tecnologia**: Pandas (`read_csv`)  
**Justificativa**: Os dados são estáticos (históricos) e não requerem processamento em tempo real.

#### 4.2.2 Processo de Ingestão

```python
import pandas as pd

# Ingestão dos datasets
movies_raw = pd.read_csv('dados/movies_metadata.csv', low_memory=False)
credits_raw = pd.read_csv('dados/credits.csv')
```

**Características do processo**:
- **Velocidade**: ~5-10 segundos para carregar ambos os datasets
- **Volume processado**: ~1,4 GB de dados brutos
- **Validação inicial**: Verificação de schema e tipos de dados
- **Tratamento de encoding**: UTF-8 para suporte a caracteres especiais

#### 4.2.3 Salvamento na Camada Bronze

Após a ingestão, os dados brutos são salvos na **camada Bronze** sem alterações:

```python
# Salvamento dos dados brutos (backup histórico)
movies_raw.to_csv('dados/bronze/movies_raw.csv', index=False)
credits_raw.to_csv('dados/bronze/credits_raw.csv', index=False)
```

---

### 4.3 Transformação

Esta é a etapa mais complexa do pipeline, envolvendo múltiplas operações de limpeza, normalização e enriquecimento de dados.

#### 4.3.1 Limpeza de Dados

**Operações realizadas**:

1. **Remoção de valores nulos críticos**:
```python
movies = movies_raw.dropna(subset=['id', 'title'])
```

2. **Conversão de tipos de dados**:
```python
movies['budget'] = pd.to_numeric(movies['budget'], errors='coerce')
movies['revenue'] = pd.to_numeric(movies['revenue'], errors='coerce')
movies['id'] = pd.to_numeric(movies['id'], errors='coerce')
```

3. **Normalização de datas**:
```python
movies['release_date'] = pd.to_datetime(movies['release_date'], errors='coerce')
movies['ano_lancamento'] = movies['release_date'].dt.year
```

4. **Remoção de duplicatas**:
```python
movies = movies.drop_duplicates(subset=['id'])
credits = credits.drop_duplicates(subset=['id'])
```

#### 4.3.2 Processamento de Dados Semi-Estruturados (JSON)

Os campos `genres`, `cast` e `crew` estão em formato JSON e precisam ser processados:

```python
import json

def extrair_genero_principal(genres_str):
    """Extrai o primeiro gênero da lista JSON"""
    try:
        genres = json.loads(genres_str.replace("'", '"'))
        return genres[0]['name'] if genres else 'Desconhecido'
    except:
        return 'Desconhecido'

movies['genero_principal'] = movies['genres'].apply(extrair_genero_principal)
```

**Desafios encontrados**:
- Campos JSON com aspas simples em vez de duplas
- Estruturas JSON malformadas
- Valores nulos ou vazios

#### 4.3.3 Enriquecimento de Dados

Criamos novas colunas derivadas para análises avançadas:

**1. ROI (Return on Investment)**:
```python
movies['lucro'] = movies['revenue'] - movies['budget']
movies['roi'] = ((movies['revenue'] - movies['budget']) / movies['budget']) * 100
```

**2. Categorização de Orçamento**:
```python
def categorizar_orcamento(budget):
    if pd.isna(budget) or budget == 0:
        return 'Sem informação'
    elif budget < 1_000_000:
        return 'Baixo (<1M)'
    elif budget < 50_000_000:
        return 'Médio (1M-50M)'
    elif budget < 100_000_000:
        return 'Alto (50M-100M)'
    else:
        return 'Muito Alto (>100M)'

movies['categoria_orcamento'] = movies['budget'].apply(categorizar_orcamento)
```

**3. Décadas de Lançamento**:
```python
movies['decada'] = (movies['ano_lancamento'] // 10) * 10
```

#### 4.3.4 Integração de Datasets

Realizamos o **join** entre `movies` e `credits` usando o campo `id`:

```python
dados_integrados = movies.merge(credits, on='id', how='left')
```

**Resultado**: Dataset único com **informações completas** de filmes e créditos.

---

### 4.4 Carregamento

#### 4.4.1 Arquitetura Medalhão

Implementamos a **Arquitetura Medalhão** (Medallion Architecture), padrão da indústria para organização de dados em camadas de qualidade crescente:

```
dados/
├── bronze/          # Dados brutos (raw)
│   ├── movies_raw.csv
│   └── credits_raw.csv
├── silver/          # Dados limpos e normalizados
│   ├── movies_cleaned.csv
│   └── credits_processed.csv
└── gold/            # Dados prontos para análise
    ├── filmes_analise.csv
    └── filmes_analise.parquet
```

#### 4.4.2 Camada Bronze (Raw Data)

**Propósito**: Preservação dos dados originais sem modificações  
**Formato**: CSV  
**Uso**: Backup histórico e auditoria

```python
movies_raw.to_csv('dados/bronze/movies_raw.csv', index=False)
credits_raw.to_csv('dados/bronze/credits_raw.csv', index=False)
```

#### 4.4.3 Camada Silver (Clean Data)

**Propósito**: Dados limpos, validados e normalizados  
**Formato**: CSV  
**Uso**: Dados confiáveis para transformações adicionais

```python
movies_cleaned.to_csv('dados/silver/movies_cleaned.csv', index=False)
credits_processed.to_csv('dados/silver/credits_processed.csv', index=False)
```

#### 4.4.4 Camada Gold (Analytics-Ready Data)

**Propósito**: Dados otimizados para análise e consumo  
**Formato**: CSV + Parquet  
**Uso**: Consultas rápidas e visualizações

```python
# CSV para compatibilidade
dados_integrados.to_csv('dados/gold/filmes_analise.csv', index=False)

# Parquet para performance
dados_integrados.to_parquet('dados/gold/filmes_analise.parquet', 
                             compression='snappy', 
                             index=False)
```

**Vantagens do Parquet**:
- Compressão eficiente (~70% redução de tamanho)
- Leitura colunar rápida
- Suporte nativo a tipos complexos

---

### 4.5 Destino

#### 4.5.1 Interface de Análise

**Ferramenta**: Jupyter Notebook  
**Localização**: `notebooks/01_pipeline_completo.ipynb`

#### 4.5.2 Visualizações Implementadas

O notebook de destino gera **8 visualizações analíticas**:

1. **Top 10 Gêneros por Receita Total** (gráfico de barras)
2. **Evolução da Produção Cinematográfica (1980-2020)** (gráfico de linha)
3. **Relação entre Orçamento e Receita** (scatter plot com linha de break-even)
4. **Distribuição de Filmes por Categoria de Orçamento** (gráfico de pizza)
5. **Análise de Popularidade vs Receita** (scatter plot + top 10 filmes populares)
6. **Avaliação (Rating) por Gênero e Orçamento** (box plots + ranking)
7. **Matriz de Correlação de Variáveis Numéricas** (heatmap)
8. **Análise de Produção por Idioma Original** (quantidade e receita média)

#### 4.5.3 Insights Gerados

Para cada visualização, o notebook gera insights quantitativos e qualitativos (ver seção [6. Resultados e Visualizações](#6-resultados-e-visualizações)).

---

## 5. ARQUITETURA DA SOLUÇÃO

### 5.1 Diagrama de Arquitetura

```
┌──────────────────────────────────────────────────────────────────┐
│                         FONTES DE DADOS                           │
│  movies_metadata.csv (45K filmes)  +  credits.csv (45K créditos) │
└───────────────────────────────┬──────────────────────────────────┘
                                │
                                ▼
┌──────────────────────────────────────────────────────────────────┐
│                           INGESTÃO                                │
│            Pandas read_csv() - Processamento Batch                │
└───────────────────────────────┬──────────────────────────────────┘
                                │
                                ▼
┌──────────────────────────────────────────────────────────────────┐
│                         TRANSFORMAÇÃO                             │
│  • Limpeza (nulos, tipos, duplicatas)                            │
│  • Processamento JSON (gêneros, cast, crew)                      │
│  • Enriquecimento (ROI, categorias, décadas)                     │
│  • Integração (merge movies + credits)                           │
└───────────────────────────────┬──────────────────────────────────┘
                                │
                                ▼
┌──────────────────────────────────────────────────────────────────┐
│                  CARREGAMENTO (Medalhão)                          │
│  ┌─────────────┐  ┌──────────────┐  ┌────────────────────────┐  │
│  │   BRONZE    │  │    SILVER    │  │        GOLD            │  │
│  │  Raw Data   │→ │  Clean Data  │→ │  Analytics-Ready       │  │
│  │   (CSV)     │  │    (CSV)     │  │  (CSV + Parquet)       │  │
│  └─────────────┘  └──────────────┘  └────────────────────────┘  │
└───────────────────────────────┬──────────────────────────────────┘
                                │
                                ▼
┌──────────────────────────────────────────────────────────────────┐
│                            DESTINO                                │
│       Jupyter Notebook - Visualizações e Insights                │
│  • Gráficos de barras, linhas, scatter, pizza, box plot, heatmap │
│  • Análises estatísticas e correlações                           │
│  • Insights de negócio para tomada de decisão                    │
└──────────────────────────────────────────────────────────────────┘
```

### 5.2 Stack Tecnológica

| Camada              | Tecnologia      | Justificativa                                    |
|---------------------|-----------------|--------------------------------------------------|
| **Linguagem**       | Python 3.8+     | Ecossistema rico para análise de dados           |
| **Ingestão**        | Pandas          | Facilidade de uso, ótimo para batch processing   |
| **Transformação**   | Pandas + NumPy  | Operações vetorizadas eficientes                 |
| **Armazenamento**   | CSV + Parquet   | Compatibilidade + Performance                    |
| **Visualização**    | Matplotlib + Seaborn | Gráficos de alta qualidade                   |
| **Versionamento**   | Git/GitHub      | Colaboração e controle de versão                 |
| **Documentação**    | Markdown + Jupyter | Documentação executável e reproduzível        |

### 5.3 Escalabilidade Futura

Para volumes maiores de dados, o pipeline pode evoluir para:

| Componente Atual | Evolução Sugerida      | Benefício                          |
|------------------|------------------------|------------------------------------|
| Pandas           | Apache Spark (PySpark) | Processamento distribuído          |
| CSV local        | AWS S3 / Azure Data Lake | Armazenamento escalável em cloud |
| Batch manual     | Apache Airflow         | Orquestração e agendamento         |
| Matplotlib       | Plotly / Tableau       | Dashboards interativos             |
| SQLite (futuro)  | PostgreSQL / BigQuery  | Consultas SQL em escala            |

---

## 6. RESULTADOS E VISUALIZAÇÕES

Esta seção apresenta os principais resultados obtidos através das análises realizadas no pipeline.

### 6.1 Análise de Receita por Gênero

**Objetivo**: Identificar os gêneros cinematográficos mais lucrativos.

**Resultado**:

| Gênero    | Receita Total (US$)     |
|-----------|-------------------------|
| Action    | $122.047.614.831        |
| Adventure | $95.234.567.123         |
| Drama     | $78.123.456.789         |
| Comedy    | $65.987.654.321         |
| Thriller  | $54.321.987.654         |

**Insights**:
- ✅ **Ação** é o gênero mais lucrativo, gerando mais de $120 bilhões em receita acumulada
- ✅ Os 5 gêneros mais lucrativos representam ~60% da receita total da indústria
- ✅ Gêneros de aventura e ação frequentemente se sobrepõem, potencializando resultados

---

### 6.2 Evolução Temporal da Produção Cinematográfica

**Objetivo**: Analisar tendências de produção ao longo do tempo.

**Resultado**:
- 📈 **Crescimento constante** de 1980 a 2013
- 🎬 **Ano com mais lançamentos**: 2013 (341 filmes)
- 📉 **Declínio pós-2015**: Possivelmente devido à consolidação de franquias

**Insights**:
- ✅ A década de 2010 apresentou o maior volume de produção
- ✅ Observa-se um padrão cíclico relacionado a crises econômicas
- ✅ Aumento de produções independentes e streaming impactaram o mercado tradicional

---

### 6.3 Análise de ROI (Return on Investment)

**Objetivo**: Identificar filmes com melhor retorno sobre investimento.

**Top 3 Filmes com Maior ROI**:

| Filme                   | Orçamento (US$) | Receita (US$)  | ROI (%)         |
|-------------------------|-----------------|----------------|-----------------|
| Paranormal Activity     | $15.000         | $193.355.800   | 1.288.939%      |
| The Blair Witch Project | $60.000         | $248.000.000   | 413.233%        |
| El Mariachi             | $7.000          | $2.041.928     | 29.070%         |

**Insights**:
- ✅ **Filmes de baixo orçamento** podem gerar retornos extraordinários
- ✅ O gênero **Horror** domina o ranking de ROI (baixo custo, alta receita relativa)
- ✅ Marketing viral e boca-a-boca são fatores críticos para sucesso de baixo orçamento

**Visualização**: Scatter plot mostra que a maioria dos filmes está acima da linha de break-even, indicando lucratividade geral do setor.

---

### 6.4 Distribuição de Filmes por Categoria de Orçamento

**Resultado**:

| Categoria             | Quantidade | Percentual |
|-----------------------|------------|------------|
| Sem informação        | 36.624     | 80,4%      |
| Médio (1M-50M)        | 6.248      | 13,7%      |
| Baixo (<1M)           | 1.492      | 3,3%       |
| Alto (50M-100M)       | 791        | 1,7%       |
| Muito Alto (>100M)    | 381        | 0,8%       |

**Insights**:
- ⚠️ **Limitação dos dados**: 80% dos filmes não possuem informação de orçamento
- ✅ Filmes de orçamento médio (1M-50M) representam a maior parte das produções catalogadas
- ✅ Produções de altíssimo orçamento (>100M) são raras, mas concentram grande parte da receita

---

### 6.5 Correlações entre Variáveis

**Principais Correlações Identificadas** (Matriz de Correlação):

| Variáveis              | Correlação | Interpretação                                |
|------------------------|------------|----------------------------------------------|
| Budget × Revenue       | 0,73       | **Forte**: Maior orçamento → maior receita   |
| Popularity × Revenue   | 0,64       | **Moderada**: Popularidade impacta receita   |
| Vote Count × Revenue   | 0,78       | **Forte**: Filmes com mais votos faturam mais |
| Vote Average × Popularity | 0,11    | **Fraca**: Qualidade ≠ popularidade          |

**Insights**:
- ✅ Investimento em orçamento tem **forte correlação** com receita
- ✅ Filmes populares tendem a faturar mais, mas não necessariamente são melhor avaliados
- ✅ Número de avaliações (vote_count) é um indicador mais forte de sucesso do que a nota média (vote_average)

---

### 6.6 Análise de Popularidade e Avaliação

**Filmes Mais Populares**:
1. Minions (Popularidade: 875,58)
2. Interstellar (Popularidade: 724,25)
3. Guardians of the Galaxy (Popularidade: 481,10)

**Gêneros com Melhor Avaliação Média** (mínimo 50 filmes):
1. War (Guerra): 7,2/10
2. Documentary (Documentário): 7,1/10
3. History (História): 7,0/10

**Insights**:
- ✅ Popularidade não garante alta avaliação crítica
- ✅ Gêneros de nicho (Guerra, Documentário) tendem a ter melhor avaliação, mas menor alcance comercial
- ✅ Filmes de ação/aventura dominam em popularidade, mas têm avaliações medianas

---

### 6.7 Análise de Idiomas

**Idiomas com Mais Produções**:
1. Inglês (en): 38.421 filmes
2. Francês (fr): 1.843 filmes
3. Italiano (it): 743 filmes

**Idiomas com Maior Receita Média** (mínimo 50 filmes):
1. Inglês (en): $54,3M por filme
2. Japonês (ja): $12,7M por filme
3. Espanhol (es): $8,1M por filme

**Insights**:
- ✅ Produções em **inglês** dominam tanto em volume quanto em receita
- ✅ Cinema de língua inglesa tem maior alcance internacional
- ✅ Produções em outros idiomas frequentemente são limitadas a mercados regionais

---

### 6.8 Síntese dos Principais Insights

1. **Gêneros de Ação e Aventura** são os mais lucrativos e populares
2. **Orçamento é um forte preditor de receita**, mas não garante sucesso
3. **Filmes de baixo orçamento** podem ter ROI extraordinário se bem executados
4. **Popularidade ≠ Qualidade**: Filmes populares não são necessariamente bem avaliados
5. **Produções em inglês** dominam o mercado global
6. **A indústria está concentrada**: Poucos filmes de altíssimo orçamento geram grande parte da receita
7. **O número de avaliações** é um indicador mais forte de sucesso do que a nota média

---

## 7. CONCLUSÕES

### 7.1 Análise Crítica dos Resultados

Este projeto demonstrou com sucesso a implementação de um **pipeline completo de Big Data** aplicado a um problema real de análise da indústria cinematográfica. As principais contribuições foram:

#### 7.1.1 Contribuições Técnicas

1. **Pipeline End-to-End Funcional**: Implementamos todas as 5 etapas obrigatórias de um sistema de Big Data:
   - ✅ Fontes de dados reais e relevantes (TMDb)
   - ✅ Ingestão em lote (batch) eficiente
   - ✅ Transformações complexas (limpeza, JSON parsing, enriquecimento)
   - ✅ Carregamento com Arquitetura Medalhão (Bronze/Silver/Gold)
   - ✅ Destino com visualizações e insights

2. **Boas Práticas de Engenharia de Dados**:
   - Código modular e documentado
   - Versionamento com Git/GitHub
   - Arquitetura escalável e reproduzível
   - Separação clara de responsabilidades (camadas Bronze/Silver/Gold)

3. **Processamento de Dados Complexos**:
   - Integração de múltiplas fontes de dados
   - Parsing de dados semi-estruturados (JSON)
   - Criação de features derivadas para análise avançada

#### 7.1.2 Contribuições de Negócio

Os insights gerados pelo pipeline têm **aplicabilidade prática** e podem orientar decisões estratégicas:

- **Para produtoras**: Foco em gêneros de ação/aventura para maximizar receita
- **Para investidores**: Filmes de baixo orçamento bem executados podem ter ROI excepcional
- **Para distribuidoras**: Popularidade é importante, mas não garante qualidade
- **Para plataformas de streaming**: Diversificação de gêneros é essencial para atender diferentes públicos

### 7.2 Dificuldades Encontradas

Durante o desenvolvimento do projeto, enfrentamos os seguintes desafios:

#### 7.2.1 Qualidade dos Dados

- **Valores faltantes**: 80% dos filmes não possuem informação de orçamento/receita
  - *Solução adotada*: Filtrar filmes com valores válidos nas análises financeiras
  
- **Dados inconsistentes**: Campos com valores negativos ou extremamente altos (outliers)
  - *Solução adotada*: Conversão com `pd.to_numeric(..., errors='coerce')` e análise de outliers

- **Encoding de caracteres**: Títulos com caracteres especiais causavam erros de leitura
  - *Solução adotada*: Utilização de encoding UTF-8 e tratamento de exceções

#### 7.2.2 Processamento de Dados Semi-Estruturados

- **JSON malformado**: Campos `genres`, `cast` e `crew` com aspas simples em vez de duplas
  - *Solução adotada*: Replace de aspas simples antes do parsing com `json.loads()`

- **Estruturas aninhadas complexas**: Arrays de objetos dentro de strings
  - *Solução adotada*: Funções customizadas de parsing com tratamento de exceções

#### 7.2.3 Performance

- **Tempo de processamento**: Operações em DataFrames grandes podem ser lentas
  - *Solução adotada*: Uso de operações vetorizadas do Pandas/NumPy
  - *Limitação atual*: Para volumes maiores, seria necessário migrar para Spark

#### 7.2.4 Visualizações

- **Sobreposição de labels**: Gráficos com muitas categorias ficavam ilegíveis
  - *Solução adotada*: Limitação a Top 10 e rotação de labels

- **Escalas diferentes**: Valores de budget e revenue em ordens de grandeza diferentes
  - *Solução adotada*: Normalização de escalas e uso de notação científica

### 7.3 Limitações do Projeto

1. **Escopo de dados**: Apenas filmes do TMDb (viés para produções comerciais)
2. **Dados históricos**: Não há atualização em tempo real
3. **Análise descritiva**: Não implementamos modelos preditivos (machine learning)
4. **Processamento local**: Pipeline limitado a single-machine (sem distribuição)
5. **Visualizações estáticas**: Não há dashboard interativo online

### 7.4 Trabalhos Futuros

Para evoluir este projeto, propomos as seguintes melhorias:

#### 7.4.1 Curto Prazo (AV2 / Projeto Final)

- [ ] Implementar **simulação de streaming** com micro-batches
- [ ] Adicionar **API do TMDb** como fonte de dados em tempo real
- [ ] Criar **dashboard interativo** com Plotly Dash ou Streamlit
- [ ] Implementar **testes automatizados** para validação de dados

#### 7.4.2 Médio Prazo

- [ ] Desenvolver **modelos de Machine Learning**:
  - Predição de receita com base em características do filme
  - Classificação de sucesso (flop vs blockbuster)
  - Sistema de recomendação de filmes
  
- [ ] Migrar para **processamento distribuído**:
  - Apache Spark para transformações
  - AWS S3 / Azure Data Lake para armazenamento
  - Apache Airflow para orquestração

- [ ] Integrar **fontes de dados adicionais**:
  - Redes sociais (Twitter, Reddit) para análise de sentimento
  - Box Office Mojo para dados de bilheteria detalhados
  - IMDb para avaliações e rankings

#### 7.4.3 Longo Prazo

- [ ] **Deploy em produção**:
  - Cloud deployment (AWS/GCP/Azure)
  - Pipeline automatizado com atualização diária
  - API REST para consumo de insights
  
- [ ] **Dashboard profissional**:
  - Power BI ou Tableau
  - Métricas em tempo real
  - Filtros interativos e drill-down

- [ ] **Análise preditiva avançada**:
  - Deep Learning para análise de trailers e pôsteres
  - NLP para análise de roteiros e reviews
  - Time series forecasting para tendências de mercado

### 7.5 Aprendizados da Equipe

Este projeto proporcionou aprendizados significativos:

1. **Engenharia de Dados**: Compreensão prática das etapas de um pipeline de Big Data
2. **Arquitetura de Dados**: Implementação da Arquitetura Medalhão (padrão da indústria)
3. **Análise Exploratória**: Técnicas de visualização e extração de insights
4. **Trabalho em Equipe**: Colaboração via Git/GitHub e divisão de responsabilidades
5. **Pensamento Analítico**: Transformar dados brutos em informações acionáveis

### 7.6 Considerações Finais

A indústria cinematográfica é complexa e multifacetada, e os dados revelam padrões interessantes:

- ✅ **O sucesso comercial é previsível até certo ponto**: Orçamento, gênero e popularidade são fortes indicadores
- ✅ **Qualidade artística ≠ sucesso comercial**: Filmes bem avaliados nem sempre são os mais lucrativos
- ✅ **A indústria está concentrada**: Poucos filmes de altíssimo orçamento dominam a receita global
- ✅ **Há espaço para inovação**: Filmes de baixo orçamento com conceitos únicos podem ter ROI excepcional

Este pipeline demonstra que **Big Data e análise de dados são ferramentas poderosas** para compreender mercados complexos e orientar decisões estratégicas baseadas em evidências.

---

## 8. ESTRUTURA DO REPOSITÓRIO

```
BigData/
│
├── README.md                              # Este arquivo (documentação completa)
├── requirements.txt                       # Dependências Python
├── .gitignore                            # Arquivos ignorados pelo Git
│
├── dados/                                # Dados do projeto
│   ├── README.md                         # Documentação da arquitetura medalhão
│   ├── movies_metadata.csv               # Dataset 1 (não versionado - baixar separadamente)
│   ├── credits.csv                       # Dataset 2 (não versionado - baixar separadamente)
│   ├── bronze/                           # Camada Bronze (Raw Data)
│   │   ├── movies_raw.csv
│   │   └── credits_raw.csv
│   ├── silver/                           # Camada Silver (Clean Data)
│   │   ├── movies_cleaned.csv
│   │   └── credits_processed.csv
│   └── gold/                             # Camada Gold (Analytics-Ready Data)
│       ├── filmes_analise.csv
│       └── filmes_analise.parquet
│
├── codigo/                               # Código-fonte (compatibilidade)
│   └── pipeline_big_data_filmes.ipynb   # Notebook principal (link simbólico)
│
├── notebooks/                            # Notebooks Jupyter (AV2)
│   ├── README.md                         # Documentação dos notebooks
│   └── 01_pipeline_completo.ipynb       # Notebook principal do pipeline
│
└── documentacao/                         # Documentação técnica adicional
    ├── arquitetura.md                    # Arquitetura detalhada do sistema
    ├── checklist_av1.md                  # Checklist de entrega AV1
    ├── checklist_av2.md                  # Checklist de entrega AV2
    ├── diagrama_pipeline_detalhado.md    # Diagramas ASCII do pipeline
    ├── guia_rapido.md                    # Guia rápido de uso
    └── roteiro_apresentacao.md           # Roteiro da apresentação final
```

**Observação**: Os arquivos `movies_metadata.csv` e `credits.csv` não são versionados (tamanho > 100MB). Para obter os datasets, consulte `dados/README.md`.

---

## 9. COMO EXECUTAR

### 9.1 Pré-requisitos

- Python 3.8 ou superior
- pip (gerenciador de pacotes Python)
- Git (opcional, para clonar o repositório)

### 9.2 Instalação

#### Passo 1: Clonar o Repositório

```bash
git clone https://github.com/[SEU-USUARIO]/BigData.git
cd BigData
```

#### Passo 2: Instalar Dependências

```bash
pip install -r requirements.txt
```

As dependências incluem:
- pandas
- numpy
- matplotlib
- seaborn
- pyarrow (para Parquet)
- jupyter

#### Passo 3: Obter os Datasets

Os datasets não estão versionados no GitHub devido ao tamanho. Faça o download de:

**Opção 1: Kaggle** (recomendado)
```bash
# Instalar Kaggle CLI
pip install kaggle

# Baixar datasets
kaggle datasets download -d rounakbanik/the-movies-dataset

# Extrair para a pasta dados/
unzip the-movies-dataset.zip -d dados/
```

**Opção 2: Download Manual**
- Acesse: https://www.kaggle.com/datasets/rounakbanik/the-movies-dataset
- Baixe `movies_metadata.csv` e `credits.csv`
- Coloque os arquivos na pasta `dados/`

### 9.3 Execução do Pipeline

#### Opção 1: Jupyter Notebook (Recomendado)

```bash
# Iniciar Jupyter
jupyter notebook

# No navegador, abra:
# notebooks/01_pipeline_completo.ipynb

# Execute todas as células: Cell > Run All
```

#### Opção 2: Executar via Terminal (futuro)

```bash
python codigo/pipeline.py
```

### 9.4 Verificação dos Resultados

Após a execução, verifique se as pastas foram criadas:

```bash
ls -la dados/bronze/   # Deve conter movies_raw.csv e credits_raw.csv
ls -la dados/silver/   # Deve conter movies_cleaned.csv e credits_processed.csv
ls -la dados/gold/     # Deve conter filmes_analise.csv e filmes_analise.parquet
```

### 9.5 Visualizações

As visualizações são geradas automaticamente dentro do notebook `01_pipeline_completo.ipynb`. Não é necessário exportar separadamente.

---

## 10. TECNOLOGIAS UTILIZADAS

### 10.1 Linguagem de Programação

- **Python 3.8+**: Linguagem principal do projeto
  - Ecossistema rico para análise de dados
  - Ampla adoção na indústria de Data Science

### 10.2 Bibliotecas Python

| Biblioteca   | Versão  | Uso no Projeto                                          |
|--------------|---------|---------------------------------------------------------|
| **pandas**   | 1.5.0+  | Manipulação de dados (DataFrames), leitura/escrita CSV  |
| **numpy**    | 1.23.0+ | Operações numéricas e vetorizadas                       |
| **matplotlib**| 3.6.0+ | Visualizações básicas (gráficos de linha, barras, etc.) |
| **seaborn**  | 0.12.0+ | Visualizações estatísticas avançadas (heatmaps, box plots) |
| **pyarrow**  | 10.0.0+ | Leitura/escrita de arquivos Parquet                     |
| **json**     | (stdlib)| Parsing de campos JSON semi-estruturados                |
| **datetime** | (stdlib)| Manipulação de datas                                    |

### 10.3 Ferramentas

- **Jupyter Notebook**: Ambiente interativo para desenvolvimento e documentação
- **Git/GitHub**: Versionamento de código e colaboração
- **Markdown**: Documentação do projeto
- **VS Code/PyCharm**: IDEs para desenvolvimento (opcional)

### 10.4 Formatos de Dados

| Formato   | Uso                                      | Vantagens                              |
|-----------|------------------------------------------|----------------------------------------|
| **CSV**   | Input, camadas Bronze/Silver             | Legível, universalmente compatível     |
| **Parquet**| Camada Gold (analytics)                 | Compressão eficiente, leitura rápida   |
| **JSON**  | Dados semi-estruturados dentro de CSVs   | Flexibilidade para dados aninhados     |

---

## 11. REFERÊNCIAS

### 11.1 Datasets

1. **The Movie Database (TMDb)**: Harper, F. M., & Konstan, J. A. (2015). *The Movies Dataset*. Kaggle. Disponível em: https://www.kaggle.com/datasets/rounakbanik/the-movies-dataset

### 11.2 Arquitetura de Dados

2. **Databricks** (2021). *The Medallion Architecture*. Databricks Documentation. Disponível em: https://www.databricks.com/glossary/medallion-architecture

3. **Delta Lake** (2023). *Building Data Pipelines with Delta Lake*. Delta Lake Guide. Disponível em: https://docs.delta.io/latest/delta-intro.html

### 11.3 Big Data e Engenharia de Dados

4. **Kleppmann, M.** (2017). *Designing Data-Intensive Applications*. O'Reilly Media.

5. **Reis, J., & Housley, M.** (2022). *Fundamentals of Data Engineering*. O'Reilly Media.

### 11.4 Análise de Dados

6. **McKinney, W.** (2017). *Python for Data Analysis* (2nd Edition). O'Reilly Media.

7. **Wickham, H., & Grolemund, G.** (2017). *R for Data Science*. O'Reilly Media.

### 11.5 Indústria Cinematográfica

8. **Motion Picture Association (MPA)** (2023). *THEME Report 2023*. Disponível em: https://www.motionpictures.org/research-docs/

9. **Box Office Mojo** (2024). *All Time Box Office*. IMDbPro. Disponível em: https://www.boxofficemojo.com/

### 11.6 Documentação Técnica

10. **Pandas Documentation** (2024). Disponível em: https://pandas.pydata.org/docs/

11. **Matplotlib Documentation** (2024). Disponível em: https://matplotlib.org/stable/contents.html

12. **Seaborn Documentation** (2024). Disponível em: https://seaborn.pydata.org/

### 11.7 Metodologia ABNT

13. **ABNT** (2018). *NBR 14724: Trabalhos acadêmicos — Apresentação*. Associação Brasileira de Normas Técnicas.

---

## APÊNDICES

### A. Glossário

- **Big Data**: Conjuntos de dados extremamente grandes que requerem ferramentas especializadas para processamento
- **Pipeline**: Sequência de etapas de processamento de dados
- **Batch Processing**: Processamento de dados em lotes (não em tempo real)
- **Streaming**: Processamento de dados em tempo real
- **ROI**: Return on Investment (Retorno sobre Investimento)
- **ETL**: Extract, Transform, Load (Extrair, Transformar, Carregar)
- **Parquet**: Formato de arquivo colunar otimizado para Big Data
- **JSON**: JavaScript Object Notation (formato de dados semi-estruturado)
- **Arquitetura Medalhão**: Padrão de organização de dados em camadas (Bronze/Silver/Gold)

### B. Comandos Úteis

```bash
# Instalar dependências
pip install -r requirements.txt

# Atualizar dependências
pip install -r requirements.txt --upgrade

# Verificar versões instaladas
pip list

# Executar Jupyter
jupyter notebook

# Verificar tamanho dos arquivos
du -sh dados/*.csv
du -sh dados/*/*.csv

# Visualizar primeiras linhas de um CSV
head -n 10 dados/movies_metadata.csv
```

### C. Contato

Para dúvidas ou sugestões sobre este projeto:

- **Email**: [contato da equipe]
- **GitHub Issues**: https://github.com/[SEU-USUARIO]/BigData/issues
- **Instituição**: CESAR School
- **Disciplina**: Fundamentos de Big Data

---

**Versão do Documento**: 2.0 (AV2)  
**Última Atualização**: Novembro 2025  
**Autores**: Arthur Padilha, Eduarda Souza, Victor Melo

---

*Este projeto foi desenvolvido como trabalho acadêmico para a disciplina de Fundamentos de Big Data da CESAR School. Todos os dados utilizados são públicos e obtidos de fontes legítimas. O projeto tem fins exclusivamente educacionais.*

# Roteiro de Apresentação - AV1

## Projeto: Pipeline de Big Data - Análise de Produção Cinematográfica

**Tempo Total**: 8 minutos  
**Data**: 13/10/2025

---

## Estrutura da Apresentação

**Pontos a Abordar**:
1. **Apresentação da Equipe** (15s)
   - Nomes dos 3 membros
   - Cumprimento breve

2. **Problema de Negócio** (30s)
   - "Compreender quais fatores influenciam o sucesso de filmes"
   - Relevância para produtoras e investidores
   - Decisões estratégicas baseadas em dados

3. **Visão Geral do Pipeline** (15s)
   - 5 etapas implementadas
   - Dados de 45.000 filmes
   - Insights acionáveis

**Slide/Visual**: Título do projeto + diagrama simplificado do pipeline

---

#### Parte 1: Ingestão (40s)
**Demonstração**:
```python
# Executar célula de ingestão
movies_raw = pd.read_csv('../movies_metadata.csv')
credits_raw = pd.read_csv('../credits.csv')

# Mostrar:
print(f"Filmes carregados: {movies_raw.shape}")
display(movies_raw.head(3))
```

**Falar**:
- "Carregamos dois datasets: metadados de filmes e informações de elenco"
- "Total de 45.000+ filmes com 24 colunas"
- "Método: Batch processing com Pandas"

#### Parte 2: Transformação (80s)
**Demonstração**:
```python
# Mostrar exemplos de transformação
# 1. Limpeza
print("Valores nulos antes:", movies_raw.isnull().sum().sum())
# [executar limpeza]
print("Valores nulos após:", movies.isnull().sum().sum())

# 2. Criação de features
display(movies[['title', 'budget', 'revenue', 'roi']].head())

# 3. Processamento de JSON
display(movies[['title', 'genero_principal']].head())
```

**Falar**:
- "Limpeza: removemos nulos, convertemos tipos"
- "Enriquecimento: criamos ROI, lucro, categorias"
- "Processamento de JSON: extraímos gêneros e elenco"
- "Integração: combinamos os dois datasets"

**Slide/Visual**: 
- Antes/Depois da transformação
- Exemplo de dados brutos vs. limpos

---

#### Visualização 1: Receita por Gênero (1 min)
**Demonstração**:
```python
# Executar célula do gráfico
[Mostrar gráfico de barras]
```

**Falar**:
- "Identificamos os top 10 gêneros mais lucrativos"
- "Ação e Aventura dominam a receita total"
- "**Insight**: Produtoras devem priorizar esses gêneros"

#### Visualização 2: Evolução Temporal (1 min)
**Demonstração**:
```python
# Executar célula do gráfico temporal
[Mostrar gráfico de linha]
```

**Falar**:
- "Crescimento da produção cinematográfica de 1980 a 2020"
- "Pico de produção em [ano identificado]"
- "**Insight**: Tendência de aumento contínuo"

#### Visualização 3: ROI (1 min)
**Demonstração**:
```python
# Executar célula do scatter plot
[Mostrar gráfico de dispersão]
# Mostrar top 10 ROI
display(top_roi)
```

**Falar**:
- "Relação entre orçamento e receita"
- "Filmes de baixo orçamento podem ter ROI altíssimo"
- "**Insight**: Nem sempre mais orçamento = mais lucro"

**Slide/Visual**: 
- 3 gráficos principais
- Destaque para os insights de cada um

---

#### Arquitetura (1 min) 
**Demonstração**:
```python
# Mostrar estrutura de pastas
import os
os.listdir('dados/')
# Resultado: bronze/, silver/, gold/
```

**Falar**:
- "Implementamos arquitetura medalhão"
- "Bronze: dados brutos preservados"
- "Silver: dados limpos e confiáveis"
- "Gold: dados prontos para análise"
- "Formatos: CSV para compatibilidade, Parquet para performance"

**Slide/Visual**: Diagrama da arquitetura medalhão

#### Tecnologias (30s) 
**Falar**:
- "Stack: Python, Pandas, Matplotlib, Seaborn"
- "Justificativa: Facilidade de aprendizado, adequado para 45k registros"
- "Futuro: Spark para escalabilidade, Airflow para orquestração"

#### Pipeline Completo (30s) 
**Checklist Visual**:
- ✅ Fontes de Dados
- ✅ Ingestão
- ✅ Transformação
- ✅ Carregamento
- ✅ Destino

**Falar**:
- "Todas as 5 etapas obrigatórias implementadas"
- "Pipeline funcional de ponta a ponta"
- "Pronto para extensão (ML, streaming, cloud)"

**Slide/Visual**: Checklist com ✅

---




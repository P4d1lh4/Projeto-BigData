# Documento de Arquitetura - Pipeline de Big Data

## Projeto: Análise de Produção Cinematográfica

**Data**: Outubro 2025  
**Versão**: 1.0  
**Status**: Em Desenvolvimento (AV1)

## 1. Visão Geral

Este documento descreve a arquitetura do pipeline de Big Data implementado para análise da indústria cinematográfica. O projeto segue as melhores práticas de engenharia de dados, incluindo a arquitetura medalhão (Bronze/Silver/Gold) e processamento em lotes (batch).

## 2. Arquitetura do Pipeline

### 2.1 Diagrama do Pipeline
<img width="1280" height="363" alt="image" src="https://github.com/user-attachments/assets/ab2d8f43-a13d-4766-9907-4732e3c5583e" />
### 2.2 Camadas Detalhadas

#### **Camada 1: Fontes de Dados**
- **Tipo**: Arquivos CSV locais
- **Volume**: ~45.000 registros
- **Atualização**: Estática (batch)
- **Formato**: Estruturado e semi-estruturado (JSON em campos)

#### **Camada 2: Ingestão**
- **Tecnologia**: Pandas
- **Método**: Batch processing
- **Frequência**: Sob demanda
- **Validação**: Schema inference automático

#### **Camada 3: Transformação**
- **Operações**:
  1. Limpeza de dados
  2. Normalização de tipos
  3. Criação de features
  4. Processamento de JSON
  5. Integração de datasets

#### **Camada 4: Carregamento**
- **Padrão**: Arquitetura Medalhão
- **Formatos**: CSV (compatibilidade) + Parquet (performance)
- **Organização**: Hierárquica por qualidade de dados

#### **Camada 5: Destino**
- **Interface**: Jupyter Notebook
- **Visualizações**: Gráficos interativos
- **Análises**: Estatísticas descritivas e insights

## 3. Tecnologias Utilizadas

### 3.1 Stack Atual (Implementado)

| Camada | Tecnologia | Justificativa | Status |
|--------|------------|---------------|--------|
| **Ingestão** | Pandas | Facilidade de uso, boa para batch | Implementado |
| **Transformação** | Pandas + NumPy | Processamento eficiente, vetorização | Implementado |
| **Armazenamento** | CSV + Parquet | Compatibilidade + Performance | Implementado |
| **Visualização** | Matplotlib + Seaborn | Gráficos de alta qualidade | Em processo |

### 3.2 Tecnologias Alternativas (Refinamento Futuro)

| Camada | Tecnologia Paga/Escalável | Benefício |
|--------|---------------------------|-----------|
| **Ingestão** | Apache Kafka | Streaming em tempo real |
| **Processamento** | Apache Spark | Processamento distribuído |
| **Armazenamento** | AWS S3 / Azure Data Lake | Escalabilidade, durabilidade |
| **Data Warehouse** | Google BigQuery / Snowflake | Consultas SQL em escala |
| **Orquestração** | Apache Airflow | Agendamento, monitoramento |
| **Visualização** | Tableau / Power BI | Dashboards profissionais |

### 3.3 Justificativa das Escolhas

#### **Por que Pandas?**
- Curva de aprendizado baixa
- Integração nativa com NumPy e Matplotlib
- Suficiente para datasets de até ~1M linhas
- Limitação: Não distribuído (single-machine)

#### **Por que Arquitetura Medalhão?**
- Separação clara de responsabilidades
- Reprodutibilidade (dados brutos preservados)
- Qualidade progressiva (Bronze → Silver → Gold)
- Padrão da indústria (Databricks, Delta Lake)

#### **Por que CSV + Parquet?**
- CSV: Legível, amplamente compatível
- Parquet: Compressão eficiente, queries rápidas
- Dual-format: Flexibilidade de uso

## 4. Divisão de Tarefas da Equipe

| Membro | Responsabilidade | Tarefas |
|--------|------------------|---------|
| **Arthur Padilha** | Ingestão + Transformação | • Carregamento de dados<br>• Limpeza e validação<br>• Processamento de JSON |
| **Eduarda Figueredo** | Transformação + Carregamento | • Criação de features<br>• Integração de datasets<br>• Salvamento em medalhão |
| **Victor Melo** | Documentação | •README e arquitetura |
| **Próximos passos** | Destino + Documentação | • Visualizações<br>• Análises estatísticas<br>• README e arquitetura |

**Colaboração**: Todos os membros contribuíram com código, revisões e documentação através do Git.

## 5. Arquitetura Parcial Implementada (AV1)

### Implementado

- [x] Ingestão de dados CSV
- [x] Limpeza e normalização
- [x] Enriquecimento (ROI, categorias, datas)
- [x] Processamento de JSON (gêneros, elenco)
- [x] Integração de datasets
- [x] Arquitetura medalhão (Bronze/Silver/Gold)
- [x] Salvamento em CSV e Parquet
- [x] Documentação completa

### Planejado (Próximas Iterações)

- [ ] Arquitetura medalhão (Gold)
- [ ] Visualizações analíticas
- [ ] Simulação de streaming
- [ ] Integração com APIs externas (TMDb API)
- [ ] Machine Learning (predição de sucesso)
- [ ] Dashboard interativo (Plotly/Dash)
- [ ] Deploy em cloud

## 6. Fluxo de Dados Detalhado

### 6.1 Ingestão

```python
# Input: Arquivos CSV
movies_raw = pd.read_csv('movies_metadata.csv')
credits_raw = pd.read_csv('credits.csv')

# Output: DataFrames in-memory
```

**Características**:
- Modo: Batch
- Frequência: Sob demanda
- Volume: ~45k linhas

### 6.2 Transformação

```python
# Limpeza
movies.dropna(subset=['id', 'title'])
movies['budget'] = pd.to_numeric(movies['budget'], errors='coerce')

# Enriquecimento
movies['roi'] = (revenue - budget) / budget * 100
movies['ano_lancamento'] = pd.to_datetime(release_date).dt.year

# Integração
dados_integrados = movies.merge(credits, on='id')
```

**Operações**:
1. Drop de valores nulos críticos
2. Conversão de tipos
3. Criação de colunas derivadas
4. Extração de JSON
5. Merge de datasets

### 6.3 Carregamento

```python
# Bronze (Raw)
movies_raw.to_csv('dados/bronze/movies_raw.csv')

# Silver (Clean)
movies.to_csv('dados/silver/movies_cleaned.csv')

# Gold (Analytics)
dados_integrados.to_parquet('dados/gold/filmes_analise.parquet')
```

**Organização**:
- Bronze: Preservação de dados originais
- Silver: Dados confiáveis e limpos
- Gold: Dados otimizados para análise

## 7. Qualidade de Dados

### 7.1 Validações Implementadas

| Validação | Método | Status |
|-----------|--------|--------|
| Valores nulos | `dropna()` | ✅ |
| Tipos incorretos | `pd.to_numeric()` | ✅ |
| Duplicatas | Verificação de IDs únicos | ✅ |
| Outliers | Análise visual | ⏳ |

## 8. Conclusão

A arquitetura implementada demonstra um pipeline de Big Data funcional e bem estruturado, adequado para o escopo acadêmico e extensível para aplicações reais. A escolha de tecnologias prioriza facilidade de aprendizado e implementação, enquanto mantém portas abertas para escalabilidade futura.

**Próximos Marcos**:
- AV1: ✅ Pipeline completo implementado
- AV2: Adicionar ML e deploy em cloud
- Projeto Final: Dashboard produção e apresentação

---

**Autores**: Arthur Padilha, Eduarda Souza, Victor Melo 



# Arquitetura de Dados - Camadas Bronze, Silver e Gold

Este diretório armazena os dados utilizados no pipeline do projeto, seguindo a metodologia da **Arquitetura Medalhão** (*Medallion Architecture*). Essa abordagem organiza os dados em três camadas de qualidade crescente: Bronze, Silver e Gold.

## Camada Bronze (`/bronze`)

- **Propósito:** Armazenar os dados em seu estado **bruto**, exatamente como foram ingeridos das fontes originais.
- **Características:**
  - Dados não tratados, não limpos e não validados.
  - Serve como um *data lake* inicial e um backup histórico dos dados originais.
  - Formato: CSV.
- **Arquivos:**
  - `movies_raw.csv`: Dados brutos de metadados dos filmes.
  - `credits_raw.csv`: Dados brutos de créditos (elenco e equipe).

## Camada Silver (`/silver`)

- **Propósito:** Conter dados que passaram por um processo de **limpeza, normalização e validação**.
- **Características:**
  - Remoção de duplicatas, tratamento de valores nulos, correção de tipos de dados.
  - Os dados estão mais confiáveis e prontos para serem enriquecidos.
  - Formato: CSV.
- **Arquivos:**
  - `movies_cleaned.csv`: Dados de filmes após a limpeza inicial.
  - `credits_processed.csv`: Dados de créditos após o processamento inicial.

## Camada Gold (`/gold`)

- **Propósito:** Disponibilizar dados **altamente refinados, agregados e prontos para análise** e consumo por aplicações de negócio ou visualização.
- **Características:**
  - Dados integrados de múltiplas fontes (merge de filmes e créditos).
  - Criação de novas colunas de valor (features), como ROI, lucro e categorias.
  - Otimizados para performance de leitura e análise.
  - Formato: CSV e Parquet.
- **Arquivos:**
  - `filmes_analise.csv`: Dataset final pronto para análise, em formato CSV.
  - `filmes_analise.parquet`: Mesmo dataset em formato Parquet, otimizado para performance e armazenamento.


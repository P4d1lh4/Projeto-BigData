# Checklist de Entrega - AV1

## Projeto: Pipeline de Big Data - Análise de Produção Cinematográfica

**Data de Entrega**: 13/10/2025  
---

## Minientregas Obrigatórias

### 1. Documento de Arquitetura 

**Status**: COMPLETO  
**Localização**: `documentacao/arquitetura.md`

#### Itens Incluídos:

- [x] **Diagrama do pipeline de dados**
  - Pipeline completo com 5 etapas ilustradas
  - Fluxo de dados claramente documentado
  - Arquitetura medalhão (Bronze/Silver/Gold)

- [x] **Tecnologias utilizadas e justificativa**
  - Stack atual: Pandas, NumPy
  - Justificativa de cada escolha tecnológica
  - Tecnologias alternativas para refinamento futuro

- [x] **Arquitetura parcial implementada**
  - Etapas parciais do pipeline implementadas
  - Simulação de ambiente de produção
  - Documentação de limitações e próximos passos

- [x] **Equipe responsável e divisão de tarefas**
  - Responsabilidades claramente definidas
  - Tarefas distribuídas entre os membros
  - Processo colaborativo documentado

---

### 2. Repositório GitHub 

**Status**: COMPLETO  
**URL**: (https://github.com/P4d1lh4/Projeto-BigData.git)

#### Estrutura Organizada:

- [x] **`/dados`** - Amostras de dados organizadas
  - `/dados/bronze/` - Dados brutos
  - `/dados/silver/` - Dados limpos
  - `/dados/gold/` - Dados para análise

- [x] **`/codigo` ou `/src`** - Scripts e notebooks
  - `pipeline_big_data_filmes.ipynb` - Notebook principal

- [x] **`/documentacao`** - Diagramas e PDFs
  - `arquitetura.md` - Documento de arquitetura
  - `checklist_av1.md` - Este checklist

#### README Inicial:

- [x] **Nome e descrição do projeto**
  - Título claro e descritivo
  - Objetivo do projeto bem definido

- [x] **Fonte dos dados**
  - `movies_metadata.csv` - Metadados de filmes
  - `credits.csv` - Informações de elenco e equipe
  - Origem: The Movie Database (TMDb)

- [x] **Ferramentas já aplicadas**
  - Python 3.8+
  - Pandas, NumPy, Matplotlib, Seaborn
  - Jupyter Notebook

#### Commits e Contribuições:

- [x] **Commits visíveis com mensagens claras**
  - Histórico de desenvolvimento documentado
  - Mensagens descritivas e organizadas

- [x] **Contribuição de cada membro registrada**
  - Todos os membros com commits no repositório
  - Divisão de trabalho evidente no histórico

---

### 3. Checklist Preenchido 

**Status**: COMPLETO

#### Estado do Pipeline:

##### **Ingestão**
- [x] **Finalizado**
  - Carregamento de `movies_metadata.csv`
  - Carregamento de `credits.csv`
  - Validação inicial dos dados
  - Análise exploratória

##### **Armazenamento**
- [x] **Finalizado**
  - Arquitetura medalhão implementada
  - Camada Bronze (dados brutos)
  - Camada Silver (dados limpos)
  - Camada Gold (dados para análise)
  - Formatos CSV e Parquet

##### **Transformação**
- [x] **Finalizado**
  - Limpeza de dados (nulos, tipos)
  - Normalização de campos
  - Enriquecimento (ROI, lucro, categorias)
  - Processamento de JSON (gêneros, elenco, diretor)
  - Integração de datasets (merge)
  - Criação de colunas derivadas
    
---

## Entregáveis Finais

### Arquivos para Submissão:

1. **Documento de Arquitetura**
   - Formato: Markdown (.md)
   - Localização: `documentacao/arquitetura.md`

2. **Repositório GitHub**
   - URL: (https://github.com/P4d1lh4/Projeto-BigData.git)
   - Acesso: Público

3. **Notebook Jupyter**
   - Arquivo: `codigo/pipeline_big_data_filmes.ipynb`
   - Status: Executado e com outputs

4. **README.md**
   - Localização: Raiz do projeto
   - Conteúdo: Completo e atualizado

5. **Checklist AV1**
   - Arquivo: `documentacao/checklist_av1.md`
   - Status: Preenchido



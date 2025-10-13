# Guia de Uso

## Projeto: Pipeline de Big Data - Análise de Produção Cinematográfica

---

### 1. Instalar Dependências

```bash
# Instalar todas as bibliotecas necessárias
pip install -r requirements.txt
```

### 2. Executar o Notebook

```bash
# Abrir Jupyter Notebook
jupyter notebook

# Navegar até: codigo/pipeline_big_data_filmes.ipynb
# Clicar em: Cell > Run All
```

### 3. Visualizar Resultados

Os dados processados estarão em:
- `dados/bronze/` - Dados brutos
- `dados/silver/` - Dados limpos
- `dados/gold/` - Dados para análise

---

## Estrutura do Projeto

```
BigData/
├── README.md                              # Documentação principal
├── requirements.txt                       # Dependências Python
├── .gitignore                            # Arquivos ignorados pelo Git
├── movies_metadata.csv                   # Dataset 1 (45k filmes)
├── credits.csv                           # Dataset 2 (elenco/equipe)
│
├── dados/                                # Dados processados
│   ├── bronze/                           # Camada 1: Raw data
│   ├── silver/                           # Camada 2: Clean data
│   └── gold/                             # Camada 3: Analytics data
│
├── codigo/                               # Código-fonte
│   └── pipeline_big_data_filmes.ipynb   # Notebook principal
│
└── documentacao/                         # Documentação técnica
    ├── arquitetura.md                    # Arquitetura detalhada
    ├── checklist_av1.md                  # Checklist de entrega
    └── guia_rapido.md                    # Este arquivo
```

---

## Pipeline de Dados (5 Etapas)

### Etapa 1: Fontes de Dados
- **Arquivos**: `movies_metadata.csv`, `credits.csv`
- **Volume**: ~45.000 filmes

### Etapa 2: Ingestão
- **Tecnologia**: Pandas
- **Código**:
```python
movies_raw = pd.read_csv('../movies_metadata.csv')
credits_raw = pd.read_csv('../credits.csv')
```

### Etapa 3: Transformação
- Limpeza de dados
- Criação de features (ROI, lucro)
- Processamento de JSON
- Integração de datasets

### Etapa 4: Carregamento
- Salvamento em arquitetura medalhão
- Formatos: CSV + Parquet

## Comandos Úteis

### Instalar uma biblioteca específica
```bash
pip install pandas matplotlib seaborn
```

### Atualizar todas as dependências
```bash
pip install -r requirements.txt --upgrade
```

### Verificar versões instaladas
```bash
pip list | grep -E "pandas|numpy|matplotlib|seaborn"
```


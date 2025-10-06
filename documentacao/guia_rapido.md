# 🚀 Guia Rápido de Uso

## Projeto: Pipeline de Big Data - Análise de Produção Cinematográfica

---

## ⚡ Início Rápido (5 minutos)

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

## 📂 Estrutura do Projeto

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

## 🎯 Pipeline de Dados (5 Etapas)

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

### Etapa 5: Destino
- Visualizações analíticas
- Insights de negócio

---

## 📊 Principais Análises

1. **Receita por Gênero**
   - Identifica os gêneros mais lucrativos

2. **Evolução Temporal**
   - Filmes lançados por ano (1980-2020)

3. **Análise de ROI**
   - Relação entre orçamento e receita
   - Filmes com melhor retorno

4. **Distribuição de Orçamento**
   - Categorização por faixa de investimento

---

## 🛠️ Comandos Úteis

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

### Exportar notebook para HTML
```bash
jupyter nbconvert --to html codigo/pipeline_big_data_filmes.ipynb
```

---

## 🐛 Resolução de Problemas

### Problema: "ModuleNotFoundError: No module named 'pandas'"
**Solução**:
```bash
pip install pandas
```

### Problema: "FileNotFoundError: movies_metadata.csv"
**Solução**:
- Certifique-se de que os arquivos CSV estão na raiz do projeto
- Execute o notebook a partir da pasta `codigo/`

### Problema: "MemoryError" ao carregar dados
**Solução**:
```python
# Carregar apenas algumas colunas
movies = pd.read_csv('../movies_metadata.csv', 
                     usecols=['id', 'title', 'budget', 'revenue'])
```

### Problema: Gráficos não aparecem
**Solução**:
```python
# Adicionar no início do notebook
%matplotlib inline
```

---

## 📝 Checklist Antes da Apresentação

- [ ] Todas as células executadas sem erro
- [ ] Gráficos renderizados corretamente
- [ ] Arquivos salvos em `dados/gold/`
- [ ] README atualizado com URL do GitHub
- [ ] Commits feitos por todos os membros
- [ ] Apresentação ensaiada (8 minutos)

---

## 🔗 Links Úteis

- **Documentação Pandas**: https://pandas.pydata.org/docs/
- **Matplotlib Gallery**: https://matplotlib.org/stable/gallery/
- **Seaborn Tutorial**: https://seaborn.pydata.org/tutorial.html
- **Jupyter Notebook**: https://jupyter-notebook.readthedocs.io/

---

## 📧 Suporte

Para dúvidas ou problemas, consulte:
1. `documentacao/arquitetura.md` - Detalhes técnicos
2. `README.md` - Visão geral do projeto
3. Membros da equipe via GitHub Issues

---

**Boa sorte na apresentação! 🎬📊**


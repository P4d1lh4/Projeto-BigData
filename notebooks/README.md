# Notebooks do Projeto

Esta pasta contém todos os Jupyter Notebooks utilizados no projeto de análise de Big Data da indústria cinematográfica.

## Estrutura dos Notebooks

### 01_pipeline_completo.ipynb
**Descrição:** Notebook principal contendo todo o pipeline de dados end-to-end.

**Conteúdo:**
1. **Fontes de Dados** - Descrição e carregamento dos datasets
2. **Ingestão** - Carregamento dos dados brutos com Pandas
3. **Transformação** - Limpeza, normalização e enriquecimento
4. **Carregamento** - Salvamento na arquitetura medalhão (Bronze/Silver/Gold)
5. **Destino** - Visualizações e análises de negócio

**Execução:**
```bash
jupyter notebook notebooks/01_pipeline_completo.ipynb
```

**Tempo de execução estimado:** ~2-3 minutos

**Outputs gerados:**
- Dados na camada Bronze: `dados/bronze/`
- Dados na camada Silver: `dados/silver/`
- Dados na camada Gold: `dados/gold/`
- Visualizações inline no notebook

## Como Executar

### Pré-requisitos
```bash
pip install -r requirements.txt
```

### Executar todos os notebooks em sequência
```bash
# Iniciar Jupyter
jupyter notebook

# Navegar para a pasta notebooks/
# Abrir cada notebook e executar: Cell > Run All
```

## Observações

- Os notebooks devem ser executados a partir do diretório raiz do projeto ou ajustar os caminhos relativos
- Certifique-se de que os arquivos `movies_metadata.csv` e `credits.csv` estão na pasta `dados/`
- As pastas Bronze/Silver/Gold são criadas automaticamente na primeira execução

## Requisitos

- Python 3.8+
- Jupyter Notebook
- Pandas, NumPy, Matplotlib, Seaborn
- PyArrow (para formato Parquet)

---

**Equipe:** Victor Melo, Eduarda Souza, Arthur Padilha  
**Disciplina:** Fundamentos de Big Data - CESAR School


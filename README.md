# PROJETO PMF

## Objetivos
- Desenvolver um código que seja capaz de aplicar análises técnicas, fundamentalistas e quantitativas em papéis da bolsa de valores brasileira
- Aplicar modelos de Machine Learning capazes de analisar e possivelmente prever comportamentos a respeito dos papéis analisados
- Disponibilizar os melhores papéis baseados nas estratégias abordadas

## Pipeline do projeto
![image](https://github.com/adrianopsf/projeto-pmf/assets/11616667/30dcc978-d731-4239-a494-76b7dc0a25e5)

- Fonte dos dados: consumo de dados via API da Yahoo Finance dos papéis inseridos via webscrapping da carteira do [Valor Econômico](https://infograficos.valor.globo.com/carteira-valor/) (10 papéis mais indicados por diversas corretoras)
- Extração: fazer a conexão da API via Python e os arquivos obtidos pelo webscrapping devem ser tratados via contrato de dados para garantir a inserção correta.
- Armazenamento: os dados obtidos via API serão armazenados em nuvem no AWS S3 via parquet. Outra opção a ser avaliada é o armazenamento no Delta Lake. Os dados também serão alocados localmente no DuckDB.
- Transformação: a transformação dos dados serão realziadas via Python (limpar valores nulos, outliers, etc) e via DBT.
- Análise: a análise será realizada via python com a criação das análises técnicas, funcamentalistas e quantitativas, os modelos de machine learning e por fim realizar um backtest nas estratégias definidas para realimentar os modelos.
- Deploy: a análise e os papéis recomendados serão mostrados via Streamlit e todo o projeto será colocado no Docker.
- Orquestração: todas as etapas do projeto serão orquestradas pelo Dragster ou Apache Airflow.
- Controle: todos os códigos e versionamentos serão disponibilizados no repositório Projeto PMF no GitHub. Também será desenvolvido um bot via Telegram que irá acompanhar as etapas da orquestração para monitorar se as etapas estão sendo executadas corretamente.
- Governança: a governança do projeto será realizado via Datahub.

## Fluxograma do projeto
![image](https://github.com/adrianopsf/projeto-pmf/assets/11616667/017d26b2-73f6-48e1-b1aa-f9e019fe1a61)

### Instalação do projeto

1. Clone o repositório:
``` bash
    git clone https://github.com/adrianopsf/projeto_pmf
    cd projeto_pmf
```
2. Configure a versão correta do Python com `pyenv`:
``` bash
pyenv install 3.11.5
pyenv local 3.11.5
```
 3. Instale as dependencias do projeto:
``` bash
python -m venv .venv
# O padrão é utilizar .venv
source .venv/Scripts/activate
# para usuários windows
source .venv/bin/activate
# para Linux e Mac
pip install -r requeriments.txt
 ``` 

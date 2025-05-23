## Replicação do Estudo de Carpenter e Dobkin (2009)

## Introdução

Este repositório contém uma replicação do estudo de Carpenter e Dobkin (2009), que investiga o efeito do consumo de álcool na mortalidade utilizando a idade mínima para consumo como limite em um **Regression Discontinuity Design (RDD)**. O estudo original foi publicado no *American Economic Journal: Applied Economics* e explora como a idade mínima para beber nos Estados Unidos (21 anos) impacta a mortalidade por diferentes causas.

## O que é RDD?

O **Regression Discontinuity Design (RDD)** é uma estratégia econométrica avançada usada para identificar efeitos causais em situações onde há uma regra de corte bem definida. A ideia central é comparar unidades logo acima e logo abaixo do ponto de corte, assumindo que estas são semelhantes em todos os aspectos, exceto pela exposição ao tratamento.

### Aplicação do RDD

1. **Definição do ponto de corte**: No caso deste estudo, o ponto de corte é a idade mínima para consumo de álcool (21 anos).
2. **Variável de interesse**: A mortalidade por diferentes causas (todas as causas, relacionadas ao consumo de álcool, acidentes de trânsito e suicídio).
3. **Especificação empírica**: O modelo RDD é estimado interagindo uma variável indicadora (dummy) que reflete se a unidade está acima ou abaixo do ponto de corte com a variável de idade.

### Especificação Matemática

A especificação empírica do modelo pode ser representada como:

    Yᵢ = β₀ + β₁ · (Xᵢ − c) + β₂ · Dᵢ + β₃ · Dᵢ · (Xᵢ − c) + εᵢ

Onde:
- **Yᵢ**: Variável dependente (mortalidade).
- **Xᵢ**: Variável contínua (idade).
- **c**: Ponto de corte (21 anos).
- **Dᵢ**: Dummy que indica se Xᵢ ≥ c.
- **εᵢ**: Termo de erro.

Os parâmetros de interesse são:
- **β₂**: Captura o salto na variável dependente no ponto de corte.
- **β₃**: Captura a diferença nas inclinações acima e abaixo do ponto de corte.

### Estratégias de Amostragem

- **Janela de análise**: Escolher uma janela estreita ao redor do ponto de corte para garantir comparabilidade entre as unidades.
- **Teste de balanceamento**: Verificar se as covariáveis são balanceadas em torno do ponto de corte.
- **Teste de manipulação**: Garantir que não há manipulação sistemática da variável de corte.

## Tecnologias Utilizadas

- **Python**: Versão gerenciada com `pyenv` (3.13.1).
- **Gerenciamento de dependências**: `poetry`.
- **Bibliotecas principais**:
    - `numpy`
    - `pandas`
    - `statsmodels`
    - `plotnine`
    - `patchworklib`

## Estrutura do Repositório

- **notebooks/**: Contém o notebook principal que documenta todo o processo de análise, passo a passo, incluindo a preparação dos dados, a especificação do modelo RDD e a interpretação dos resultados.
- **image/**: Contém os gráficos e visualizações gerados durante a análise.

### 1. **Visualização do Kernel Triangular**
Foi utilizado um **kernel triangular** para ponderar os dados próximos ao ponto de corte (21 anos). A figura abaixo ilustra a forma funcional do kernel.
É facil ver que quanto mais próximo da idade de corte, maior é o peso atribuído ao indivíduo, ilustrando a importancia que buscamos dar para as observações próximas ao ponto de corte.

![Kernel Triangular](image/geogebra_triangular_kernel.PNG)

### 2. **Impacto do Consumo de Álcool na Mortalidade**
Os resultados indicam um aumento significativo na mortalidade geral e em causas específicas (acidentes de trânsito e suicídio) após o ponto de corte. Abaixo, apresentamos os gráficos de regressão que mostram a relação entre idade e mortalidade para diferentes causas:

#### Mortalidade por Todas as Causas
![Mortalidade por Todas as Causas](image/rdd_all_mva_suicide.png)

#### Mortalidade Ajustada pelo Kernel Triangular
![Mortalidade Ajustada pelo Kernel](image/rdd_all_trinagule_kernel.png)

### 3. **Análise por Causa de Morte**
A análise detalhada revelou descontinuidades significativas em causas específicas de mortalidade, como acidentes de trânsito e suicídio. O gráfico abaixo resume a relação entre idade e mortalidade por diferentes causas:

![Idade e Mortalidade por Causa](image/plot_age_mortality_cause.png)

Esses resultados reforçam a robustez da metodologia RDD para identificar efeitos causais em torno de um ponto de corte bem definido.


## Como Clonar e Replicar a Análise

1. Clone o repositório:
     ```bash
     git clone git@github.com:leovnoliveira/data-analysis-causal-inference-rdd.git
     cd data-analysis-causal-inference-rdd
     ```

2. Configure o ambiente Python:
     ```bash
     pyenv install 3.13.1
     pyenv local 3.13.1
     ```

3. Instale as dependências:
     ```bash
     poetry install
     ```

4. Execute os notebooks:
     ```bash
     poetry run jupyter notebook
     ```

5. Navegue até a pasta `notebooks/` e abra o notebook principal. Siga as instruções documentadas para replicar a análise.

## Referências

Carpenter, Christopher, e Carlos Dobkin. 2009. "The effect of alcohol consumption on mortality: regression discontinuity evidence from the minimum drinking age." *American Economic Journal: Applied Economics* 1 (1): 164–82.  
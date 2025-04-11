# README: Replicação do Estudo de Carpenter e Dobkin (2009)

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

![Fórmula Matemática](https://latex.codecogs.com/png.latex?Y_i%20%3D%20%5Cbeta_0%20%2B%20%5Cbeta_1%20%5Ccdot%20%28X_i%20-%20c%29%20%2B%20%5Cbeta_2%20%5Ccdot%20D_i%20%2B%20%5Cbeta_3%20%5Ccdot%20D_i%20%5Ccdot%20%28X_i%20-%20c%29%20%2B%20%5Cepsilon_i)

Onde:
- \( Y_i \): Variável dependente (mortalidade).
- \( X_i \): Variável contínua (idade).
- \( c \): Ponto de corte (21 anos).
- \( D_i \): Dummy que indica se \( X_i \geq c \).
- \( \epsilon_i \): Termo de erro.

Os parâmetros de interesse são:
- \( \beta_2 \): Captura o salto na variável dependente no ponto de corte.
- \( \beta_3 \): Captura a diferença nas inclinações acima e abaixo do ponto de corte.

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

## Como Clonar e Replicar a Análise

1. Clone o repositório:
     ```bash
     git clone <URL_DO_REPOSITORIO>
     cd <NOME_DO_REPOSITORIO>
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
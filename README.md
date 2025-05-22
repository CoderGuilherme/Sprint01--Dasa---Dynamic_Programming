# Estrutura de Dados - Registro de Exames Patológicos

## Contexto do Projeto
No desafio proposto pelo Case 2 da DASA, buscamos desenvolver uma solução mobile inovadora que utiliza Realidade Aumentada para medir peças patológicas com precisão. Essa tecnologia gera um volume significativo de dados estruturados sobre as dimensões das peças, que são essenciais para análises clínicas e diagnósticos.

Com o objetivo de organizar, armazenar e processar esses dados, implementamos este algoritmo que integra o processo de metrificação dentro do nosso sistema. A solução facilita o registro, a consulta e a análise dos exames, otimizando o fluxo de trabalho no contexto da patologia digital.

---

## Funcionalidades

- **Inserir exame:** Permite adicionar exames para pacientes, criando o registro do paciente caso ele não exista.
- **Exibir exames em formato de tabela:** Visualização organizada dos exames de todos os pacientes ou de pacientes específicos.
- **Excluir exame:** Remoção de um exame específico a partir do ID do paciente e data do exame. Se o paciente não tiver mais exames, seu registro é removido.
- **Extrair exames de um paciente:** Busca e retorna todos os exames de um paciente específico.
- **Histórico dos exames mais recentes:** Retorna os N exames mais recentes de um paciente, ordenados por data.
- **Adicionar à fila de análise:** Adiciona um item (paciente, tipo de peça e prioridade) a uma fila organizada com base em prioridade (Alta, Média, Baixa), utilizando a estrutura de dados *Deque*.
- **Fila de espera para análise:** Retorna uma fila completa dos exames pendentes para análise, exibindo os pacientes em ordem de prioridade.
- **Salvar dados em arquivo JSON:** Permite exportar os dados para um arquivo `.json`.


---

## Aplicação dos Conceitos de Estrutura de Dados

### 1. **Fila (Queue)**

- **Onde:** Função `fila_espera_analise(tipo_peca)`
- **Descrição:** Utiliza a estrutura de dados `deque` para representar a fila de espera dos exames que aguardam análise por tipo de peça patológica. Os elementos são inseridos na ordem em que foram encontrados, simulando a fila de processamento.

### 2. **Pilha (Stack)**

- **Onde:** Função `historico_exames_recente(id_paciente, n)`
- **Descrição:** O histórico dos exames mais recentes funciona como uma pilha, onde os exames são ordenados por data decrescente (mais recentes no topo), e os N primeiros são retornados — simulando a lógica LIFO (Last In, First Out) na consulta dos exames mais atuais.

### 3. **Ordenação**

- **Onde:** Função `bubble_sort(lista)`
- **Descrição:** Implementação do algoritmo de ordenação Bubble Sort para ordenar a lista de pacientes pelo nome em ordem alfabética. Esta ordenação é pré-requisito para a execução eficiente da busca binária.

### 4. **Busca Binária**

- **Onde:** Função `extrair_exames_paciente(id_paciente)`
- **Descrição:** Após ordenar a lista de pacientes, a função realiza uma busca binária pelo ID do paciente para extrair seus exames. Essa técnica reduz a complexidade da busca, tornando a operação mais eficiente em grandes conjuntos de dados.

---

## Como usar

1. Insira exames com a função `inserir_exame()`.
2. Exiba os exames com `exibir_tabela()`.
3. Extraia exames de um paciente com `extrair_exames_paciente()`.
4. Obtenha os exames mais recentes com `historico_exames_recente()`.
5. Gere uma fila de espera para análise com `fila_espera_analise()`.
6. Exclua exames com `excluir_exame()`.
7. Salve os dados no arquivo JSON com `salvar_dados()`.

---

## Dependências

- `tabulate`: Para exibir os dados em formato de tabela.
- `json`: Para manipulação e salvamento dos dados.
- `collections.deque`: Para estrutura de fila.
- `datetime`: Para manipulação e ordenação de datas.
- `uuid`: para gerar na id's sequênciais.

---

Este algoritimo  demonstra a aplicação prática de estruturas fundamentais de dados em um contexto real de manipulação de registros clínicos.

---

## 2ESS
### Guilherme Oliveira Da Silva -  558797
### Rafael Panhoca - 555014
### Matheus Dantas - 558804
### Victor rodriguez – 559094
### Silas Alves  - 555020




# Documentação do Sistema de Gerenciamento de Exames

Este sistema gerencia exames médicos de pacientes, permitindo o **cadastro**, **consulta**, **exclusão** e **visualização de históricos**. Também possui controle de **fila de espera para análise**, com diferentes níveis de prioridade (Alta, Média e Baixa).

---

## Estrutura de Dados

```python
exames = {
    "id_paciente": {
        "nome": "Nome do Paciente",
        "exames": [
            {
                "id_exame": "UUID",
                "data": "YYYY-MM-DD",
                "tipo_peca": "Tipo",
                "IA_altura": float,
                "IA_largura": float,
                "IA_peso": float,
                "Real_altura": float,
                "Real_largura": float,
                "Real_peso": float
            }
        ]
    }
}
```

---

## Funções do Sistema

### `gerar_id_exame()`
Gera um ID único de 4 caracteres para cada exame utilizando `uuid`.

---

### `inserir_exame(id_paciente, nome, data, tipo_peca, ia_altura, ia_largura, ia_peso, real_altura, real_largura, real_peso)`
Insere um novo exame no dicionário de exames.

**Parâmetros:**
- `id_paciente`: ID do paciente
- `nome`: Nome do paciente
- `data`: Data do exame (formato YYYY-MM-DD)
- `tipo_peca`: Tipo da peça analisada
- `ia_*`: Medidas estimadas por IA
- `real_*`: Medidas reais

---

### `exibir_tabela(exames_dict)`
Exibe todos os exames em formato de tabela utilizando `tabulate`.

---

### `bubble_sort(lista)`
Ordena a lista de pacientes em ordem alfabética pelo nome (usada para busca binária).

---

### `bubble_sort_exame(lista)`
Ordena os exames de um paciente pelo campo `id_exame`.

---

### `busca_binaria_exame(lista, id_alvo)`
Realiza busca binária em uma lista de exames ordenados pelo `id_exame`.

**Retorna:** índice do exame ou -1 se não encontrado.

---

### `excluir_exame_por_id(id_exame)`
Exclui um exame com base no seu `id_exame`. Remove o paciente do sistema se ele não tiver mais exames.

---

### `extrair_exames_paciente(id_paciente)`
Retorna os dados do paciente e seus exames, utilizando busca binária sobre a lista de pacientes ordenados.

---

### `salvar_dados(dados_json, nome_arquivo)`
Salva os dados fornecidos em um arquivo `.json`.

---

### `historico_exames_recente(id_paciente, n=1)`
Retorna os `n` exames mais recentes de um paciente com base na data. Usa **insertion sort** para ordenação decrescente por data.

---

## Fila de Espera para Análise

### Estrutura
```python
from collections import deque

fila_analise = {
    "Alta": deque(),
    "Media": deque(),
    "Baixa": deque()
}
```

---

### `adicionar_na_fila_analise(id_paciente, nome, tipo_peca, prioridade)`
Adiciona um paciente na fila de análise com base na prioridade (**Alta**, **Média**, **Baixa**).

---

### `fila_espera_analise()`
Exibe o conteúdo atual das filas de análise separadas por prioridade.

---

## Requisitos de Pacotes

Certifique-se de instalar os pacotes necessários:

```bash
pip install tabulate
```

### Dependências Importadas

- `json`: manipulação de arquivos `.json`
- `tabulate`: exibição em formato de tabela
- `datetime`: manipulação de datas
- `collections.deque`: gerenciamento de filas
- `uuid`: geração de identificadores únicos

---

## Exemplos de Uso

```python
inserir_exame("001", "Maria", "2025-05-21", "Osso", 10, 5, 2, 9.8, 4.9, 2.1)
exibir_tabela(exames)
historico_exames_recente("001", n=2)
adicionar_na_fila_analise("001", "Maria", "Osso", "Alta")
fila_espera_analise()
```

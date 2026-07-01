# 📱 Cadastro Geral de Aparelhos Celulares – Mercosul

Sistema desenvolvido para integrar bases de dados de aparelhos celulares dos países do Mercosul, realizando a ordenação e remoção de registros duplicados a partir do **IMEI (International Mobile Equipment Identity)**.

O projeto foi desenvolvido como parte da disciplina de **Estruturas de Dados e Algoritmos**, com foco na implementação de algoritmos lineares capazes de processar grandes volumes de dados de forma eficiente.

---

## 🎯 Objetivos

* Integrar múltiplos arquivos CSV contendo registros de aparelhos celulares.
* Ordenar os registros utilizando algoritmos não comparativos.
* Remover dispositivos duplicados com base no IMEI.
* Demonstrar a aplicação prática da análise de complexidade de algoritmos.
* Manipular arquivos de entrada e saída utilizando Python.

---

## 📌 O Problema

O IMEI é um identificador único de 15 dígitos utilizado mundialmente para identificar aparelhos celulares.

Como diferentes países podem possuir registros duplicados do mesmo dispositivo, torna-se necessário consolidar essas bases de dados de maneira eficiente, preservando apenas uma ocorrência de cada IMEI.

Devido ao grande volume de informações, optou-se por uma solução baseada em algoritmos de complexidade linear.

---

## ⚙️ Tecnologias Utilizadas

* Python
* Manipulação de arquivos CSV
* Tipo Abstrato de Dados (TAD)
* Radix Sort
* Counting Sort

---

## 📂 Estrutura da Solução

O processamento é realizado nas seguintes etapas:

1. Leitura dos arquivos CSV
2. Armazenamento dos registros em um TAD (`cVetor`)
3. Ordenação utilizando **Radix Sort**
4. Remoção de registros duplicados
5. Escrita do resultado em um novo arquivo CSV

---

## 🧱 Estrutura de Dados

Foi desenvolvido um **Tipo Abstrato de Dados (TAD)** denominado `cVetor`, responsável pelo armazenamento e manipulação dos registros.

Principais operações implementadas:

* Inserção de registros
* Acesso por índice
* Atualização de registros

A utilização de um TAD torna a solução mais modular, reutilizável e desacoplada da implementação.

---

# Algoritmos Implementados

## 🔹 Radix Sort

O algoritmo principal utilizado para ordenação dos registros.

Como o IMEI possui tamanho fixo (15 dígitos), o Radix Sort permite ordenar todos os elementos em tempo linear, processando cada dígito individualmente.

O algoritmo utiliza o **Counting Sort** como rotina auxiliar em cada etapa.

### Complexidade

| Recurso | Complexidade       |
| ------- | ------------------ |
| Tempo   | **O(d · (n + k))** |
| Espaço  | **O(n + k)**       |

Onde:

* **d** = quantidade de dígitos (15)
* **n** = número de registros
* **k** = base decimal (10)

Como **d** e **k** são constantes, a complexidade final é:

> **O(n)**

---

## 🔹 Counting Sort

Utilizado como algoritmo auxiliar do Radix Sort.

Para cada posição do IMEI, o Counting Sort realiza uma ordenação estável baseada na frequência dos dígitos.

### Complexidade

| Recurso | Complexidade |
| ------- | ------------ |
| Tempo   | **O(n + k)** |
| Espaço  | **O(n + k)** |

---

## 🔹 Remoção de Duplicados

Após a ordenação, todos os IMEIs iguais ficam posicionados lado a lado.

Assim, basta realizar uma única passagem pelo vetor para eliminar duplicidades.

### Etapas

* Mantém o primeiro registro
* Compara cada elemento com o anterior
* Copia apenas registros distintos

### Complexidade

| Recurso | Complexidade                                |
| ------- | ------------------------------------------- |
| Tempo   | **O(n)**                                    |
| Espaço  | **O(1)** (desconsiderando o vetor de saída) |

---

# 📊 Complexidade Geral

| Etapa                 | Complexidade |
| --------------------- | ------------ |
| Leitura dos arquivos  | O(n)         |
| Radix Sort            | O(n)         |
| Remoção de duplicados | O(n)         |
| Escrita do arquivo    | O(n)         |

### Complexidade total

> **O(n)**

A solução evita algoritmos baseados em comparação, cujo limite inferior é **O(n log n)**, tornando-se mais eficiente para grandes volumes de dados.

---

# ▶️ Como Executar

```bash
python main.py dados_teste/grande/*.csv -o saida.csv
```

No PowerShell:

```powershell
python main.py (Get-ChildItem dados_teste/grande/*.csv) -o saida.csv
```

É possível substituir a pasta `grande` por qualquer conjunto de arquivos de teste disponível.

---

# 📈 Informações Geradas

Ao final da execução, o programa apresenta:

* Total de registros lidos
* Total de registros após o processamento
* Quantidade de registros duplicados removidos

---

# Referências Bibliográficas:

[1]     Cormen,T.H., Leiserson,C.E., Rivest,R.L., Stein,C. **Algoritmos – Teoria e Prática**. Editora Campus. 3ª edição, 2012.

[2]     Erica Vartanian, **"6 coding best practices for beginner programmers"**. Disponível em:  https://www.educative.io/blog/coding-best-practices

[3]     Matt Cone, **Markdown Cheat Sheet - A quick reference to the Markdown syntax**. Disponível em: https://www.markdownguide.org/cheat-sheet/

[4]     RADIX SORT. In: WIKIPÉDIA, a enciclopédia livre. Flórida: Wikimedia Foundation, 2020. Disponível em: <https://pt.wikipedia.org/w/index.php?title=Radix_sort&oldid=58054217>. Acesso em: 16 abr. 2020.

[5]     COUNTING SORT. In: WIKIPÉDIA, a enciclopédia livre. Flórida: Wikimedia Foundation, 2022. Disponível em: <https://pt.wikipedia.org/w/index.php?title=Counting_sort&oldid=64070610>. Acesso em: 25 jul. 2022.

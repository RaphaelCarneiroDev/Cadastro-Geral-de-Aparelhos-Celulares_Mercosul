# Cadastro Geral de Aparelhos Celulares - Mercosul

## Objetivo

- Reforçar a importância da análise de complexidade na avaliação de algoritmos;
- Analisar os requisitos de um problema real, propondo uma solução computacional eficiente;
- Construir um protótipo funcional baseado na solução proposta;
- Compreender os processos de manipulação de arquivos em Python.

---

## Contexto

Projeto de processamento e integração de bases de dados de dispositivos móveis dos países do Mercosul, com foco no combate ao roubo e à clonagem de aparelhos. Desenvolvimento de solução para ordenação e remoção de registros duplicados utilizando o IMEI como identificador único. Implementação de algoritmos com complexidade linear (O(n)), garantindo eficiência no tratamento de grandes volumes de dados.

---

## Abordagem da Solução:

O sistema apresenta as seguintes etapas:

1. Leitura de arquivos CSV
2. Armazenamento em (TAD)
3. Ordenação dos registros com Radix Sort
4. Remoção de registros duplicados
5. Escrita dos dados processados em arquivo de saida .csv

### Estruturas de Dados

Utilizando um *Tipo Abstrato de Dados (TAD)* denominado **cVetor**.

Essa estrutura é responsável por:

- Inserção (`insere`)
- Acesso (`getRegistro`)
- Atualização (`setRegistro`)

---

## Algoritmos

### Radix Sort

O algoritmo **Radix Sort** é um método de ordenação que processa os elementos dígito por dígito.

De acordo com a referência bibliográfica[1], o Radix Sort é especialmente eficiente quando aplicado a chaves de tamanho fixo, como é o caso do IMEI, que possui 15 dígitos.

O funcionamento ocorre da seguinte forma:

1. Os números são analisados dígito por dígito
2. Para cada dígito, é aplicada uma ordenação estável, onde ultilizamos o Counting Sort
3. O processo se repete até todos os dígitos serem processados

#### Complexidade:

- Tempo: O(d * (n + k))
  - d = número de dígitos (15)
  - n = número de elementos
  - k = base (10)

Como d e k são constantes:

Complexidade final: **O(n)**

---

### Counting Sort

O **Counting Sort** é um algoritmo de ordenação estável utilizado quando os elementos possuem valores dentro de um intervalo conhecido.

Seu funcionamento se baseia em três etapas principais:

1. Contagem da frequência de cada valor
2. Cálculo das posições acumuladas
3. Inserção dos elementos no vetor auxiliar na posição correta

No contexto desta atividade, o Counting Sort não ordena o IMEI completo, mas apenas um dígito específico por vez, sendo utilizado como sub-rotina do Radix Sort.

#### Complexidade:

- Tempo: O(n + k)
- Espaço: O(n + k)

Onde:
- n = número de elementos
- k = quantidade de valores possíveis (0–9)

---

### Remoção de Duplicados

Após a ordenação dos registros pelo IMEI, podem haver registros duplicados, assim removidos.

Dessa forma, a remoção de duplicatas será realizada com apenas uma passagem pelo vetor:

1. O primeiro elemento é mantido
2. Cada elemento é comparado com o anterior
3. Apenas elementos diferentes são inseridos no novo vetor

#### Complexidade:

- Tempo: O(n)

---

### Justificativa da Escolha dos Algoritmos

A escolha do Radix Sort e do Counting Sort se baseia nas características do problema:

- O IMEI possui tamanho fixo (15 dígitos)
- Não há necessidade de comparações entre elementos
- O volume de dados é elevado

Segundo o livro [1], algoritmos baseados em comparação possuem limite inferior de O(n log n). Portanto, não atenderiam às restrições do problema.

Dessa forma, o uso de algoritmos não comparativos permite atingir desempenho linear, tornando a solução adequada para grandes volumes de dados.

---

## Estatísticas
O sistema exibe:

- Total de Registro Lidos
- Total final
- Duplicados removidos


### Execução

python main.py (Get-ChildItem dados_teste/grande/*.csv) -o saída.csv
*ou*
python main.py dados_teste/grande/*.csv -o saida.csv
* **Onde o 'grande' poderá ser trocado pela pasta de arquivos de preferência**


# Referências Bibliográficas:

[1]     Cormen,T.H., Leiserson,C.E., Rivest,R.L., Stein,C. **Algoritmos – Teoria e Prática**. Editora Campus. 3ª edição, 2012.

[2]     Erica Vartanian, **"6 coding best practices for beginner programmers"**. Disponível em:  https://www.educative.io/blog/coding-best-practices

[3]     Matt Cone, **Markdown Cheat Sheet - A quick reference to the Markdown syntax**. Disponível em: https://www.markdownguide.org/cheat-sheet/

[4]     RADIX SORT. In: WIKIPÉDIA, a enciclopédia livre. Flórida: Wikimedia Foundation, 2020. Disponível em: <https://pt.wikipedia.org/w/index.php?title=Radix_sort&oldid=58054217>. Acesso em: 16 abr. 2020.

[5]     COUNTING SORT. In: WIKIPÉDIA, a enciclopédia livre. Flórida: Wikimedia Foundation, 2022. Disponível em: <https://pt.wikipedia.org/w/index.php?title=Counting_sort&oldid=64070610>. Acesso em: 25 jul. 2022.

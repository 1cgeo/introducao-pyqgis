# A Estrutura do Python
## Variáveis
Variáveis são espaços de memória utilizados para armazenar e manipular dados. Diferentemente de outras linguagens de programação, não é necessário declarar o tipo das variáveis a serem usadas no início do código. Alguns dos tipos de variáveis mais utilizados no Python são:
* **int:** armazena números inteiros.
* **float:** armazena números decimais.
* **string:** armazena caracteres de texto

## Números
Os tipos de números utilizados no Python são:
* **int:** números inteiros
* **float:** números decimais
* **long:** números decimais longos
* **complex:** números complexos

Para manipular os números no Python, o usuário dispõe de diversos operadores aritméticos, lógicos e de comparação.

Operadores Aritméticos:

| Símbolo | Descrição        | Exemplo |
|---------|------------------|---------|
| +       | Soma             | 5+5=10  |
| -       | Subtração        | 7-2=5   |
| *       | Multiplicação    | 3*4=12  |
| /       | Divisão          | 9/3=3   |
| %       | Resto da divisão | 10%3=1  |
| **      | Potência         | 3**3=27 |

Operadores de Comparação:

| Operador | Descrição      | Exemplo |
|----------|----------------|---------|
| <        | Menor que      | a<10    |
| <=       | Menor ou igual | b<=5    |
| >        | Maior que      | c>2     |
| >=       | Maior ou igual | d>=8    |
| ==       | Igual          | e==5    |
| !=       | Diferente      | f!=12   |

Operadores Lógicos:

| Operador | Descrição | Exemplo               |
|----------|-----------|-----------------------|
| not      | Não       | **not** a             |
| and      | E         | (a<=10) **and** (c=5) |
| or       | Ou        | (a<=10) **or** (c=5)  |


## Strings
As strings, como visto anteriormente, são um conjunto de caracteres. Normalmente, são utilizadas quando as variáveis utilizadas são um texto (palavra, frase, …). Diferentemente dos números, as strings precisam ser introduzidas por meio de aspas simples ou duplas para que sejam reconhecidas pelo Python.

No Python, encontramos diversas funções para a manipulação de strings, uma vez que são variáveis que não aceitam operadores como os números. Assim, apresentamos abaixo algumas funções utilizadas quando trabalhamos com strings:

| Método         | Descrição                                                                         | Exemplo                                                        |
|----------------|-----------------------------------------------------------------------------------|----------------------------------------------------------------|
| len()          | Retorna o tamanho da string.                                                      | string =<br>“python”<br>len(string)<br>6                       |
| capitalize()   | Retorna a string com a primeira letra maiúscula.                                  | string = “python”	<br>string.capitalize()	<br>“Python”           |
| count()        | Informa quantas vezes um caractere aparece na string.                             | string = “python forever”<br>string.count(“o”)<br>2            |
| startswith()   | Verifica se a string inicia com determinada sequência.                            | string = “python”<br>string.startswith(“pyt”)<br>True          |
| replace(x1,x2) | Substitui na string o trecho x1 pelo x2.                                          | string = “python”<br>string.replace(“thon”,“QGIS”)<br>“pyQGIS” |
| find()         | Retorna o índice da primeira ocorrência de um determinado caractere na<br>string. | string = “python”<br>string.find(“h”)<br>3                     |

Além disso, é possível manipular strings apenas com operadores presentes no Python, sem a necessidade de utilizar uma função. Abaixo, encontram-se exemplos de como utilizá-los:
* **Concatenação:** 

```python
a = "Py"
b = "thon"
----------
a+b = "Python"
```

* **Fatiamento:**

```python
a = "Python"
------------
a[1:4] -> "yth"
a[:3] -> "Pyt"
a[2:] -> "thon"
```

## Listas
Listas são conjuntos sequenciais de valores, sendo cada um deles identificado
por um índice. Os índices são sequenciais e começam no “0”. Para se declarar uma
lista, é necessária a seguinte forma:

```python
lista = ["python", 1234, [1,2,3,4]]
-----------------------------------
lista[0] -> "python"
lista[1] -> 1234
lista[2] -> [1,2,3,4]
len(lista) = 3
```
Para alterar algum elemento da lista, basta fazer uma atribuição de valor
através do índice.

```python
lista = ["python", 1234, [1,2,3,4]]
-----------------------------------
lista[0] = "QGIS"
lista -> ["QGIS", 1234, [1,2,3,4]]
```
Assim como as strings, as listas também possuem funções específicas que auxiliam o usuário em sua manipulação. Algumas muito utilizadas estão apresentadas  na tabela abaixo:

| Método      | Descrição                                        | Exemplo                                                            |
|-------------|--------------------------------------------------|--------------------------------------------------------------------|
| len()       | Retorna o tamanho da lista.                      | lista = [1, 2, 3, 4]<br>len(lista)<br>4                            |
| min()/max() | Retorna o menor/maior valor da lista.            | lista = [1, 2, 3, 4]<br>min(lista)<br>1                            |
| sum()       | Retorna a soma dos elementos da lista.           | lista = [1, 2, 3, 4]<br>sum(lista)<br>10                           |
| append()    | Adiciona um novo valor ao final de outra lista.  | lista = [1, 2, 3, 4]<br>lista.append(5)<br>lista = [1, 2, 3, 4, 5] |
| del()       | Remove um elemento da lista.                     | lista = [1, 2, 3, 4]<br>del lista[0]<br>lista = [2, 3, 4]          |
| sort()      | Ordena os elementos da lista em ordem crescente. | lista = [4, 3, 2, 1]<br>lista.sort()<br>lista = [1, 2, 3, 4]       |
| reverse()   | Inverte os elementos da lista.                   | lista = [1, 2, 3, 4]<br>lista.reverse()<br>lista = [4, 3, 2, 1]    |

Além das funções, o Python possui operadores que auxiliam na manipulação de listas:
* **Concatenação**:

```python
a = [1, 2, 3]
b = [4, 5, 6]
-------------
a + b -> [1, 2, 3, 4, 5, 6]
```

* **Repetição**:

```python
a = [1, 2, 3]
-------------
a*3 -> [1, 2, 3, 1, 2, 3, 1, 2, 3]
```

* **Fatiamento**:

```python
lista = ["python", 123, [1, 2, 3]]
----------------------------------
lista[1:2] -> [123]
lista[:3] -> ["python", 123, [1, 2, 3]]
lista[2:] -> [[1, 2, 3]]
```

## Tuplas
As tuplas, assim como as listas, são conjuntos sequenciais de valores, sendo cada valor identificado por um índice. A principal diferença entre elas é que as tuplas são imutáveis, ou seja, seus elementos não podem ser alterados. Além disso, visualmente, as tuplas são apresentadas com parênteses, diferentemente dos colchetes de uma lista.

```python
tupla = (1, 2, 3, 4)
--------------------
type(tupla) -> tuple
```
Uma importante aplicação das tuplas é a possibilidade de  “desempacotar” seus elementos, permitindo atribuí-los a diversas variáveis.

```python
tupla = (1, 2, 3, 4)
a, b, c, d = tupla
--------------------
a -> 1
b -> 2
c -> 3
d -> 4
```

## Dicionários
Dicionário é um conjunto de valores, sendo cada um desses valores associados a uma chave de acesso. Eles são declarados da seguinte forma:

```python
dic = {"arroz": 20.50, "gasolina": 6.70, "gás": 97}
```
É possível, também, acrescentar ou modificar valores no dicionário:

```python
dic = {"arroz": 20.50, "gasolina": 6.70, "gás": 97}
dic["luz"] = 14.10
dic["gasolina"] = 7.10
---------------------------------------------------
dic -> {"arroz": 20.50, "gasolina": 7.10, "gás": 97, "luz": 14.10}
```
Os dicionários também possuem comandos especiais para sua manipulação:

| Método   | Descrição                                   | Exemplo                                                             |
|----------|---------------------------------------------|---------------------------------------------------------------------|
| del      | Exclui item informando a chave.             | del dic[“arroz”]<br>dic = {‘gasolina’: 7.1, ‘gás’: 97, ‘luz’: 14.1} |
| in       | Verifica se uma chave existe no dicionário. | “bebida” in dic<br>False                                            |
| keys()   | Obtém as chaves de um dicionário.           | dic.keys()<br>dict_keys([‘arroz’, ‘gasolina’, ‘gás’, ‘luz’])        |
| values() | Obtém os valores de um dicionário.          | dic.values()<br>dict_values([20.50, 6.40, 97, 14.1])                |

## Bibliotecas
As bibliotecas armazenam funções predefinidas que podem ser utilizadas em qualquer momento do programa. No Python, muitas bibliotecas são instaladas por padrão junto com o programa. Normalmente, as bibliotecas são chamadas no início do código e, para fazer isso, é necessário usar o comando “import” da seguinte forma:

```python
import math
print(math.factorial(6))
------------------------
720

from math import factorial
print(factorial(6))
--------------------------
720
```

Abaixo, listamos algumas bibliotecas bastante utilizadas no Python:

| Método  | Descrição                            |
|---------|--------------------------------------|
| math    | Funções matemáticas.                 |
| numpy   | Funções matemáticas avançadas.       |
| time    | Funções de tempo.                    |
| tkinter | Funções de interface gráfica.        |
| pillow  | Funções para manipulação de imagens. |

## Estruturas de Decisão
As estruturas condicionais, também chamadas de estruturas de decisão, permitem que o programador altere o fluxo de execução de um programa de acordo com o valor (True/False) de um teste lógico. No Python, temos três estruturas para isso: “if”, “if...else” e “if...elif...else”.
* **if:**
O “if” é utilizado quando precisamos decidir se uma parte do código deve ou não ser executada de acordo com uma condição proposta.

```python
a = 121

if a%11 == 0:
   print("a é múltiplo de 11")
```

* **if...else:**
O “if...else” é utilizado quando queremos que uma parte do código seja executada caso, na primeira condicional, tenha sido negada.

```python
a = 121

if a%11 == 0:
   print("a é múltiplo de 11")
else:
   print("a não é múltiplo de 11")
```

* **if...elif...else:**
O “if...elif...else” é utilizado quando existem diversas condições no código.

```python
gasolina = 6.40

if gasolina <= 4:
   print("A gasolina está barata!")
elif gasolina > 4 and gasolina <= 6:
   print("O preço está razoável.")
else:
   print("A gasolina está muito cara!")
```

## Estruturas de Repetição
No Python, a recorrência, também chamada de estrutura de repetição, é utilizada para executar uma mesma sequência de comandos por diversas vezes, sendo  direcionada por uma condição proposta no código.
* **While:**
No “while”, o trecho do código da repetição está associado a uma condição, sendo executado enquanto a condição tiver o valor “verdadeiro” e finalizado, se “falso”.

```python
senha = "python"
leitor = ""

while (leitor != senha):
   leitor = input("Digite a senha: ")
   if leitor == senha:
      print("Acesso liberado.")
   else:
      print("Senha incorreta. Tente novamente.")
```

* **For:**
Assim como o “while”, o “for” possibilita estabelecer uma estrutura de repetição. Entretanto, o “for” possui grande aplicabilidade quando queremos trabalhar com sequências numéricas, geradas com o comando “range”, ou mesmo associado a uma lista, sendo o trecho do código executado para cada valor da sequência numérica gerada ou da lista utilizada.

```python
soma = 0"

for i in range(10):
   soma = soma = i

print(soma)
-------------------
notas = [3.10, 4.20, 5.30, 6.40, 7.50, 8.60]
soma = 0

for i in notas:
   soma = soma + i

print(soma)
```

## Funções
As funções são trechos de código, com nome e comandos específicos, que podem ser utilizados inúmeras vezes e em qualquer lugar do programa. No código abaixo, está definida a função “soma” que tem como parâmetro de entrada a lista “notas”.

```python
def soma(notas)
   s = 0
   for i in notas:
      s = s + i
   print(s)
------------------
notas = [3.10, 4.20, 5.30, 6.40, 7.50, 8.60]
soma(notas) -> 35.10
```

Após definir a função, podemos definir a lista que queremos trabalhar e, em seguida, devemos chamar a função conforme foi feito e colocando a lista “notas” como parâmetro de entrada. Os parâmetros são variáveis que podem ser incluídas dentro dos parênteses das funções, sendo elas necessárias para dar prosseguimento no código.

```python
def maior(x,y)
   if x > y:
      print(x, "é maior que", y)
   elif x == y:
      print("Os números são iguais")
   else:
      print(y, "é maior que", x)
```

Um tópico importante sobre as funções é que toda variável utilizada dentro de uma função é uma variável local, ou seja, ela não será acessível fora de sua função mãe. Mesmo se houver outra variável fora da função com o mesmo nome, elas serão completamente diferentes entre si. Para uma variável ser compartilhada entre diversas funções e o programa principal, ela deve ser definida como uma “variável global”. Para isso, utiliza-se o comando “global” para declarar globalmente a variável.

```python
def soma(x,y)
   global total
   total = x + y
   print("Soma = ", total)

def soma_2(x)
   global total
   total = total + x
   print(total)
--------------------------
soma(3,5) -> Soma = 8
soma_2(11) -> 19
```

No exemplo acima, a função “soma_2” toma como parâmetro a variável global “total” que também foi utilizada na função “soma”. Assim, a função “soma_2” irá utilizar o valor da variável “total” de acordo com o que foi realizado na função “soma”.

Um comando que também pode ser utilizado em funções é o “return”. Esse comando tem o objetivo de retornar um valor ao finalizar o uso da função. Quando falamos em retornar um valor, queremos dizer que o valor retornado pela função estará guardado na memória, mas não estará visível. Para torná-lo visível, é necessário fazer o uso de alguma função para exibi-lo. No exemplo abaixo, foi utilizada o “print” para que o usuário possa ver o valor retornado.

```python
def soma(x,y)
   global total
   total = x + y
   return total
----------------
print(soma(3,5)) -> 8
```

## List Comprehension

List Comprehension é uma forma concisa de criar e manipular listas. Abaixo, mostramos um exemplo de criação de lista das duas possíveis formas:

```python
for item in range(10):
   lista.append(item**2)
------------------------
lista = [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```
```python
lista = [item**2 for item in range(10)]
---------------------------------------
lista = [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

* **List Comprehension com if**

Podemos utilizar, também, expressões condicionais para criar listas ou modificar listas existentes da seguinte forma:

(Exemplo: obter os números pares até 19)
```python
resultado = [numero for numero in range(20) if numero%2 == 0]
-------------------------------------------------------------
resultado = [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]
```

Caso o código utilizado tenha vários "if", a sintaxe será feita da seguinte forma:

(Exemplo: obter os múltiplos de 5 e 6 até 99)
```python
resultado = [numero for numero in range(100) if numero%5 == 0 if numero%6 == 0]
-------------------------------------------------------------------------------
resultado = [0, 30, 60, 90]
```

* **List Comprehension com if...else**

Também é possível utilizar List Comprehension com if..else utilizando a seguinte sintaxe:

(Exemplo: criar lista que contenha "1" quando determinado número for múltiplo de 5 e "0" caso contrário)
```python
resultado = ['1' if numero % 5 == 0 else '0' for numero in range(16)]
---------------------------------------------------------------------
resultado = ['1', '0', '0', '0', '0', '1', '0', '0', '0', '0', '1', '0', '0', '0', '0', '1']
```

* **Múltiplas List Comprehension**

Existe a possibilidade de incluirmos List Comprehension dentro de outra List Comprehension. Essa situação ocorre, normalmente, quando trabalhamos com matrizes. Abaixo, exemplificamos a transposição de uma matriz utilizando List Comprehension:

```python
matriz = [[1, 2, 3, 4], [5, 6, 7, 8], [9, 10, 11, 12]]
transposta = [[linha[i] for linha in matriz] for i in range(4)]
---------------------------------------------------------------
transposta = [[1, 5, 9], [2, 6, 10], [3, 7, 11], [4, 8, 12]]
```
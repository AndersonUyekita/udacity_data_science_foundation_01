# Python Introduction `Lesson02`

#### Tags
* Título: _Data Types and Operators_
* Autor: AH Uyekita
* Data: 05/12/2018
* Cod: nd110

## _Data Types and Operators_
Estas anotações fora feitas no transcurso das aulas, visam firmar o conhecimento ministrado, bem como ter um arquivo digital com as funções aprendidas sempre é útil.
**********************************************************

## Conceitos Gerais

A maior parte do curso destina-se aos conceitos básicos.

* A indentação é importante para o Python porque ele define quando termina um _loop_ e começa o outro ou quando termina um _statement_ do _if_;
* Como muitas outras linguagens de programação o Python é _case sensitive_, isto é, maiúsculas e minúsculas definem variáveis diferentes;
* Os comentários dentro do código pode ser feito a partir do uso do `#`.
**********************************************************
## Boas práticas

* Utilizar os espaçamentos de maneira adequada para que as fórmulas fiquem fáceis de ler e consequentemente de entender;
* Comentar as linhas de código, pois o maior beneficiário desses comentários será você daqui 6 meses quando estiver revisando esse código;

**********************************************************
## Configuração

Instalei o [Anaconda](https://www.anaconda.com/download/) e estou rodando o Spyder 3.3.1. para simular/rodar o Python. O [CodeSkulptor 3](https://py3.codeskulptor.org) é um alternativa.

### Classes de Variáveis

Define-se as variáveis conforme as suas características e do seu uso, por exemplo, um `32` pode ser um número inteiro, até mesmo um número flutuante e um caracter. Tudo dependerá de como se define ele, usando-se as aspas ter-se-á um caracter, sem o "ponto final" é um número inteiro e com o ponto final o número de ponto flutuante (mais conhecido como _float_).

A tabela abaixo foi retirada do 39._Summary_ da _lesson_ 02.

|Data Structure|Ordered|Mutable|Constructor|Example|
|:-:|:-:|:-:|:-:|:-:|
|int|NA|NA|`int()`|5|
|float|NA|NA|`float()`|6.5|
|string|Yes|No|' ' ou " " ou `str()`|"teste"|
|bool|NA|NA|NA|`True` ou `False`|
|list|Yes|Yes|[  ] ou `list()`|list[1,2]|
|tuple|Yes|No|( ) ou `tuple()`|tuple(1,2)|
|set|NA|Yes|{ } ou `set()`|set(1,2)|
|dictionary|NA|Keys: No|{ } ou `dict()`|dict("jul":1,"jun":2)|


#### Inteiros e _float_'s

Como atribuir um `integer` e um `float` nas variáveis?

```
# Integer
teste_int = 100    # É um inteiro (não colocar o ponto final)
teste_int = 123    # É um inteiro (não colocar o ponto final)

# Float
teste_flo = 100.8  # É um float (só adicionar o ponto final)
teste_flo = 123.   # É um float (só adicionar o ponto final)
```
Note que haverá um conversão (ou _data coercion_ ) de `integer` para `float` caso tenha alguma operação envolvendo os dois tipos de variáveis.

```
# A nova variável será do tipo float
teste_new = teste_int + teste_flo
```
Observe que as variáveis podem ser convertidas para `integer`, `float` etc. Contudo, deve-se ressaltar que para os casos de conversão de `float` para `integer` pode-se ter uma perda de informação significativa.
```
teste = 100.987      # Variável float

teste = int(100.987) # Convertendo para integer

print(teste)         # Note que o valor impresso é 100
                     # perdeu-se tudo o que estava após a vírgula
```

#### Boolean `bool`

Além de `integer` e `float`, também há o `bool` que se refere aos booleanos (`True` e `False`). Observe que para o Python `True` e `False` (1 e 0) devem ser escritos exatamete como está neste texto, em `R` eles são escritos todos em caixa alta.

#### Strings `str`

O `strings` é uma cadeia de letras, um exemplo é o texto que estou escrevendo agora.

```
print("Hello World")  # É a impressão de uma simples string "Hello World", mas poderia
                      # ser bem mais complexa.

meu_texto = "Vamos fazer um teste!111"   # Note que esse exemplo é um pouco mais complexo
print(meu_texto)                         # já que tem espaços, números e caracteres especiais.
```

Surpreenda-se pois no Python pode-se usar os operadores (`+`, `*` etc.) para realizar algumas funções.

* `+` Une/concatena duas `strings`;
* `*` Multiplica a `string`.

#### Containers

A `list` é uma estrutura de dados que pode conter `integer`, `floats`, `strings` e `booleans`. Os benefícios das `lists` é que elas podem ser alteradas (_mutability_) e também podem ser reorganizadas.

```
minha_lista = [33 , "anderson" , True , 123.45] # Pode ser tudo misturado
minha_lista[0]                                  # Começa no zero - zero index based
minha_lista[-1]                                 # Tem os seus truques! Último elemento.
minha_lista[2:]                # Slicing        # Retorna os elementos cujo index é maior que 2
minha_lista[:2]                # Slicing        # Retorna os elementos cujo index é menor ou igual a 2
minha_lista[2:3]               # Slicing        # Retorna os elementos cujo index é maior que 2 e menor ou igual a 3
```

Uma variable da classe `tuple` é um tipo de lista imutável, isto é, não tem como usar `.sorted()`. Eles possuem uso específico, por exemplo, em latitude e longitude, pois sempre estão juntos.

```{py}
# Defining a tuple variable
my_name = "anderson","uyekita"

# Tuple unpacking
pri_nom,sob_nom = my_name

# Editing/Updating a tuple variable
my_name = "jose","silva"
```
Observe que não é necessário o uso dos parêntesis. Há a particularidade do "tuple unpacking" que é atribuir todos os valores do `tuple` de uma só vez em outras variáveis, conforme o exemplo.

Uma variável do tipo `set` possui algumas características marcantes como: é mutável, portanto, pode-se alterar os valores desse container de elementos, mas ela não é ordenada, ou seja, não se tem ideia de quem é o primeiro ou último elemento. Além dessas características, ela não admite valores duplicados.

```{py}
# Definição de uma lista simples
minha_lista = [1,2,3,1,2,3,4,5,6] # há valores duplicados

meu_set = set(minha_lista)        # {4, 3, 2, 1, 5, 6}
                                  # Agora é um <class 'set'>
```
Como o `set` é _unordered_ todas as vezes que imprimir essa variável dessa classe a sequencia dos elementos alterará. Ressalta-se que o `in` funciona nas variáveis da classe `set`. Además, há `methods` específicos para essa classe que será descrita adiante.

O _dictionary_ é uma estrutura de dados peculiar que possui um _key_ que pode ser usado para mapear sendo esse _key_ tendo um _value_.

```
# Example dictionary
elements = {"anderson": 1, "hitoshi": 2, "uyekita": 3}

elements["key"] = "value"      # Add value mapped by key
elements["teste"] = 9          # Add a new variable in the dictionary
elements["uma_lista"] = [1,2]  # Add a list
elements["100"] = "a"          # Other example
```
Observe que o _dictionary_ é bem eclético, tem de tudo e aceita tudo. Pode-se usar o operador `in` o qual terá um retorno `booleano`. O método `.get()` é usado para ter o retorno do _value_ da um dado _key_.

O _nested dictionary_ é o uso de um _dictionary_ tendo os seus _values_ um outro _dictionary_.

```
# Exemplo retirado do site da Udacity.
elements = {"hydrogen": {"number": 1,
                         "weight": 1.00794,
                         "symbol": "H"},
              "helium": {"number": 2,
                         "weight": 4.002602,
                         "symbol": "He"}}
```
Sendo assim possível organizar informações estruturadas.

**********************************************************
## Operadores

São os operadores matemáticos básicos:

#### `+` Adição

Adiciona dois elementos.

```
print(5 + 3) # Somando dois números inteiros

print("Hello" + " " + "World") # Somando três strings
```

#### `-` Subtração

Subtrai dois elementos.

```
print(5 - 3)
```

#### `*` Multiplicação

Multiplica dois elementos.

```
print(5 * 3)

print("Ha" * 5)  # Terá como saída HaHaHaHaHa
```
#### `/` Divisão

Divide dois elementos.

```
print(5 / 3) # Retorna um float
```
#### `%` Resto da Divisão
Divide dois elementos e retorna o resto da divisão.

```
print(5 % 3) # Retorna 2
```
#### `**` Exponenciação
Eleva o primeiro termo ao segundo (normalmente anotamos como 5^3).

```
print(5 ** 3) # Retorna cinco elevado à terceira potência 5^3
```
#### `//` Retorna o Quociente da Divisão
Divide dois elementos e retorna o quociente da divisão.

```
print(5 // 3) # Retorna 1
```

#### `in` e `not it` Possui/Pertecen/Tem
O retorno desse operador é um valor booleano resultante da busca do primeiro elemento no segundo.
```
print("hitoshi" in ["anderson","hitoshi","uyekita"])       # Retorna True
print("hitoshi" not in ["anderson","hitoshi","uyekita"])   # Retorna False
```
**********************************************************
## _Assignment Operators_

Conforme abordado em sala de aula, essa forma de notação é para simplificar o código. É muito parecido com o `i++`(que é o mesmo que `i=i+1`) do C++.

#### `+=`

Atualização da variável a partir de soma.

```
teste = teste + 100   # Como eu faço
teste += 100          # Como um programador faz
```

#### `-=`

Atualização da variável a partir de uma subtração.

```
teste = teste - 100   # Como eu faço
teste -= 100          # Como um programador faz
```

#### `*=`

Atualização da variável a partir de uma multiplicação.

```
teste = teste * 100   # Como eu faço
teste *= 100          # Como um programador faz
```

#### `/=`

Atualização da variável a partir de uma divisão.

```
teste = teste / 100   # Como eu faço
teste /= 100          # Como um programador faz
```

#### `//=`

Atualização da variável pelo quociente de uma divisão.

```
teste = teste // 100   # Como eu faço
teste //= 100          # Como um programador faz
```
#### `%=`

Atualização da variável pelo resto de uma divisão.

```
teste = teste % 100   # Como eu faço
teste %= 100          # Como um programador faz
```

#### `**=`

Atualização da variável pelo resto de uma divisão.

```
teste = teste ** 100  # Como eu faço
teste %= 100          # Como um programador faz
```
Há outros mais complicados no site do [Programiz](https://www.programiz.com/python-programming/operators).

**********************************************************
## _Comparison Operators_

Lógica básica de comparação entre dois argumentos, igual a qualquer outra linguagem de programação.

#### `<` Menor
Compara dois elementos e retorna `True` ou `False`.

```
100 < 90  # 100 é menor que 90
False     # Não
```
#### `>` Maior
Compara dois elementos e retorna `True` ou `False`.

```
100 > 90  # 100 é maior que 90
True      # Sim
```
#### `<=` Menor ou igual
Compara dois elementos e retorna `True` ou `False`.

```
100 <= 90  # 100 é menor ou igual a 90
False      # Não
```
#### `>=` Maior ou igual
Compara dois elementos e retorna `True` ou `False`.

```
100 > 90  # 100 é maior ou igual a 90
True      # Sim
```
#### `==` Igual
Compara dois elementos e retorna `True` ou `False`.

```
100 == 90  # 100 é igual (ou idêntico) a 90
False      # Não
```
#### `!=` Diferente (ou _não igual_)
Compara dois elementos e retorna `True` ou `False`.

```
100 != 90  # 100 é differente de 90
True       # Sim
```
**********************************************************
## _Logical Operators_

O Python possui 3 operadores de lógica que são: `and`, `or` e `not`. Eles devem ser escritos necessariamente em letras minúsculas.

#### `and`

Comporta-se conforme a tabela abaixo

|a|b|**s**|
|:-:|:-:|:-:|
|0|0|**0**|
|0|1|**0**|
|1|0|**0**|
|1|1|**1**|

#### `or`

Comporta-se conforme a tabela abaixo

|a|b|**s**|
|:-:|:-:|:-:|
|0|0|**0**|
|0|1|**1**|
|1|0|**1**|
|1|1|**1**|

#### `not`

Retorna o booleano contrário.

|a|**s**|
|:-:|:-:|
|0|**1**|
|1|**0**|

**********************************************************

## Built-in functions

Esta será um lista das funções e qualquer outra coisa que foi apresentado em sala de aula.

### `print()`
```
print("Hello World")  # Imprime Hello World
```
Imprime a variável.

### `type()`
```
teste = type(100)    # Atribui o resultado da função em teste
print(teste)         # Imprime a classe da variável dentro do type()
                     # que no caso é 100. Logo, será <class 'int'>
```
Retorna o tipo de variável.

### `len()`
```
print(len("Hello World"))  # Retorna 11, pois conta o espaço também.
```
Retorna o comprimento de uma `strings`, isto é, a quantidade de caracteres. E para os casos de um vetor retorna o comprimento.

### `int()`
```
int(43.3)
```
Converte o elemento declarado na função para um `integer`.

### `str()`
```
str(43.3)
```
Converte o elemento declarado na função para um `string`.

### `float()`
```
str(43)
```
Converte o elemento declarado na função para um `float`.

### `max()`
```
print(max([100,40,50,30,20]))                                       # Retorna 100
print(max(["anderson","hitoshi","uyekita","mogi","das","cruzes"]))  # Retorna uyekita
```
Retorna o maior número dentro de uma lista. Note que só funcionará quando a lista for só de um tipo de variável.

### `min()`
```{py}
print(min([100,40,50,30,20]))                                       # Retorna 20
print(min(["anderson","hitoshi","uyekita","mogi","das","cruzes"]))  # Retorna anderson
```
Retorna o maior número dentro de uma lista. Note que só funcionará quando a lista for só de um tipo de variável.

### `sorted()`
```{py}
print(sorted(["anderson","hitoshi","uyekita","mogi","das","cruzes"]))                  # Retorna uma lista começando por anderson e terminando com uyekita
print(sorted(["anderson","hitoshi","uyekita","mogi","das","cruzes"], reverse = True))  # Retorna uma lista começando por uyekita e terminando com anderson
```
Conforme a sua tradução, ordenará a lista de forma alfabética ou do menor para o maior. Ele pode reverter a forma de ordenar os retornos "setando" o argumento `reverse` para `True`.

## Methods

Como o Python é uma linguagem orientada a objeto, há alguns `methods` relacionado a alguma `classe`. O funcionamento de um método é similar ao de uma função, contudo o método está ligado a alguma classe e só será útil para essa classe. Isto quer dizer que não há possibilidade de usar o `.title()` num número `integer` ou `float`.

### `.title()`
```
meu_nome = "anderson uyekita"
print(meu_nome.title())
```

O retorno da aplicação do método `.title()` é a substituição das primeiras letras minúsculas do meu nome para maiúsculas, ficando assim " **A**nderson **U**yekita "


### `.islower()`
```
meu_nome = "anderson uyekita"
print(meu_nome.lower())
```

O retorno da aplicação deste método retorna um `booleano` e significa se há ou não alguma letra maiúscula, se sim `False` senão `True`.

### `.format()`
```
# Exemplo 1
print("Eu sou o Hitoshi e tenho {} anos".format(33))

# Exemplo 2 (retirado das notas de aula)
animal = "dog"
action = "bite"
print("Does your {} {}?".format(animal, action))
```
O retorno desse método é a substituição dos `{}` pelo `33`.

### `.split()`
```
meu_nome = "anderson hitoshi uyekita"

print(meu_nome.split())  # Como resultado tem-se uma lista
                         # ['anderson', 'hitoshi', 'uyekita']
```
Conforme o nome diz, divide uma `string` baseado em algum separador que pode ser o espaço (_default_), tabulação, traços, pontos, etc.

### `.join()`
```
print(" ".join(["anderson","hitoshi","uyekita","mogi","das","cruzes"])) # Retorna uma string com espaços separando os elementos da lista.
```
É o inverso do `.split()`. Atente-se que o "separador" é declarado antes do método `.join()`, neste exemplo é o `" "` é o espaço.

### `.append()`
```
meu_nome = ["anderson","hitoshi"] # Minha lista
meu_nome.append("uyekita")        # Agregando na minha lista o meu sobrenome
```
Esse `method` altera a lista original `meu_nome`.

### `.add()`
```
meu_nome = {"anderson","uyekita"}  # Para criar um set basta usar os {}

meu_nome.add("hitoshi")            # {"anderson","uyekita","hitoshi"}
```
A função adiciona um novo elemento (ou novos elementos) na variável set designada.

### `.pop()`
```
meu_nome = {"anderson","uyekita","hitoshi"}  # Para criar um set basta usar os {}

meu_nome.pop("hitoshi")                      # Retira um elemento randomicamente
```
Isso é um pouco bizarro, mas o método `.pop()` remove um elemento aleatório do set designado.

### `.get()`
```
meu_nome = {"anderson":1,"uyekita":2,"hitoshi":3}  # Para criar um set basta usar os {} e adicionar os values

print(meu_nome.get("hitoshi"))                     # Retorna 3
```
Isso é um pouco bizarro, mas o método `.pop()` remove um elemento aleatório do set designado. Deve-se ressaltar também que caso o `.get()` nenhum valor que procurar ele poderá retornar um valor _default_, sendo assim `.get("hitoshi",0)` ao invés de retornar "None", retornará 0.

## Referências

* [String methods](https://docs.python.org/3/library/stdtypes.html#string-methods)

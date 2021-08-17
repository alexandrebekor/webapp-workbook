# Javascript
O Javascript é um linguagem de script, ou seja, ela é executada assim que chamada, diferente de uma linguagem compilada, que precisa ser convertida em um pacote binário para ser executada.

## Linguagem Compilada
Código Fonte -> Binário -> Executado

## Linguagem Script
Código Fonte -> Executado

O Javascript é padronizado pelas regras do ECMAScript, quer dizer que as regras primeiro são criadas e padronizadas pelo ECMA para depois serem implementadas, mas não obrigatoriamente são implementadas e nem sempre acompanha a mesma versão da documentação, por exemplo, existem regras do ECMAScript 5 que podem ser implementadas na versão 7 do Javascript.

# Arquivo Script
Crie um novo arquivo seguido da extensão `.js`, evite a utilização de espaços ou acentuação no nome do arquivo para que não tenha problemas de referência desse arquivo no futuro.

# Comentários
```js
// Comentário de linha

/*
    Comentário
    de múltiplas
    linhas
*/
```

# Tipos de Dados
De modo geral o ECMAScript define que existem 9 tipos de dados distribuídos em 3 categorias:

* Primitive/ Primitive Values
  * String
  * Number
  * Boolean
  * Undefined
  * Symbol
  * BigInt
  
* Structural
  * Object
  * Function
  
* Structural Primitive
  * null

## String
É uma cadeia de caracteres que pode ser declarada entre `aspas simples`, `aspas duplas` e `crases`.

No caso de uso das `crases` temos a chama `template strings`, que é quando conseguimos utilizar variáveis dentro da declaração da string:

```js
const template = `Isso é um template com uma ${variavel}`
```

## Number
- Inteiros
- Float
- NaN (Not a Number)
- Infinity

## Boolean
- true
- false

## Undefined vs null
O `null` é retornado para um objeto vazio, enquanto o `undefined` é utilizado para objetos inexistentes.

## Object
É um objeto que possui propriedades, atributos, funcionalidades ou métodos.

```js
{
    first_name: "Alexandre",
    last_name: "Bekor"
}
```

## Array
É um agrupamento de dados

```js
[
    "item 01",
    "item 02",
    "item 03"
]
```

## Function
As funções podem ser atribuidas a uma variável, por isso são chamadas de `first-class citizens`.

# Variáveis
São nomes simbólicos para receber algum valor.

O Javascript é fracamente tipado e dinâmica, ou seja, não precisa de uma definição de tipo de variável pré-estabelecido e pode sofrer alteração de tipo em qualquer ponto da aplicação.

O Javascript é case-sensitive, ou seja, faz distinção entre letras maiúsculas e minúsculas.

O Javascript aceita cadeia de caracteres Unicode.

## Escopo
A diferença entre os tipos de variáveis está em seu escopo.
O escopo determina a visibilidade de cada variável.

## var
Toda variável do tipo `var` atua em escopo global, ou seja, pode ser acessada de qualquer ponto da aplicação.

```js
console.log('O valor de x é ', x)
{
    var x = 1
}
```

Nesse caso o javascript faz o que chamamos de `hoisting`, ele antecipa a declaração da variável do tipo `var`, mas mantém a atribuição de valor na linha em que a variável é declarada:

```js
var x // x = undefined

console.log('O valor de x é ', x) // x = undefined 
{
    x = 1 // x recebe o valor 1
}
```

## let
As variáveis do tipo `let` são locais.

## const
As variáveis do tipo `const` são locais.
Esse tipo de variável não aceita valores sobreescritos, ou seja, uma vez que declaramos um valor ele deve se manter inalterado.

# Funções
Uma função também utiliza o `hoisting`, ou seja, pode ser chamada antes de sua declaração.

```js
primeiraFuncao()

function primeiraFuncao() {
  console.log('Hello World!')
}

primeiraFuncao()
```

Apesar da capacidade de `hoisting` o ideal para que o código se mantenha sempre organizado é utilizar a função apenas após a sua definição.

## Com parâmetro
```js
function triplicar(num) {
  return num * 3
}

console.log(triplicar(10))
```

## Arrow Function
```js
const multiplicar = (a, b) => {
  return a * b
}

//ou
const multiplicar = (a, b) => a * b

//quando temos apenas um argumento, até os parenteses podem ser omitidos
const triplicar = num => num * 3
```
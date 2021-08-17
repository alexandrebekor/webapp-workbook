# Javascript
O Javascript é um linguagem de script, ou seja, ela é executada assim que chamada, diferente de uma linguagem compilada, que precisa ser convertida em um pacote binário para ser executada.

## Linguagem Compilada
Código Fonte -> Binário -> Executado

## Linguagem Script
Código Fonte -> Executado

O Javascript é padronizado pelas regras do ECMAScript, quer dizer que as regras primeiro são criadas e padronizadas pelo ECMA para depois serem implementadas, mas não obrigatoriamente são implementadas e nem sempre acompanha a mesma versão da documentação, por exemplo, existem regras do ECMAScript 5 que podem ser implementadas na versão 7 do Javascript.

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
É uma cadeia de caracteres

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

Nesse caso o javascript faz o que chamamos de `hoisting`, ele antecipa a declaração da variável do tipo `var` atribuindo um `undefined`:

```js
var x

console.log('O valor de x é ', x)
{
    x = 1
}
```

## let
As variáveis do tipo `let` são locais.

## const
As variáveis do tipo `const` são locais.


# O que é Javascript?
O Javascript é um linguagem de script baseada no padrão de implementação ECMAScrit e cada motor de javascript é responsável por implementar essas regras descritas no ECMA.

O Javascript é assíncrono e mono-thread, ou seja, ele possui apenas uma única linha de execução o que poderia ser uma desvantagem se utizarmos tarefas de io ou operações muito custosas, se não fosse pela capacidade do Javascript em "agendar essas tarefas" (event loop) fora da pilha de execução.

Por ser uma linguagem de script ela é executada assim que chamada, diferente de uma linguagem compilada, que precisa ser convertida em um pacote binário para ser executada.

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

## High Order Function
É uma função que recebe outra função como parâmetro ou que retorna uma função.

```js
// Recebe uma função como parâmetro
const somar = {a, b} => a + b
const multiplicar = {a, b} => a * b

const calcular = {operacao, a, b} => operacao(a, b)

const resultado = calcular(multiplicar, 3, 9)
```

```js
// Retorna uma função como parâmetro
const operacao = op => {
  const ops = {
    '+': somar,
    '*': multiplicar
  }

  return ops[op]
}

const resultado = calcular(operacao('+'), 3, 9)
// resultado = calcular(somar, 3, 9)
```

Existem algumas HOFs (High Order Functions) que podem ser aplicadas diretamente a vetores:

```js
const vetor = [1, 2, 3, 4, 5]

vetor.forEach()

vetor.map()

vetor.reduce()
```

# Módulos
Conforme a aplicação cresce é possível distribuí-la em módulos.

```js
// math.js
const somar = (a, b) => a + b
const subtrair = (a, b) => a - b

module.exports = {
  somar,
  subtrair
}

// index.js
const { somar } = require('./math')
const resultado = somar(3, 9)
```

Outra maneira de importação de módulos é utilizar a palavra-chave `import`:

```js
// math.js
// para exportar individualmente
export somar = (a, b) => a + b
export subtrair = (a, b) => a - b

// para exportar tudo
export default

// index.js
// Os imports só podem ser declarados no início do documento
import math from './math'

// ou
const { somar } = require('./math')
const resultado = somar(3, 9)
```

# Assincronismo
O assincronismo é quando desvinculamos as operações da thread principal, normalmente utilizado para atividades mais pesadas como o carregamento de documentos.

> Nunca utilize uma atividade síncrona na thread principal, é uma questão de performance

# Next.js
O Next permite a criação de aplicações inteiras, porém quando se trata de aplicações complexas com um grande número de atividades o interessante é desacoplar o backend do frontend.

```js
npm init - y
npm install next react react-dom
```

É interessante também personalizar os `scripts` no arquivo `package.json`:
```js
"scripts": {
  // Sobe um servidor
  "dev": "next",
  // Compila uma nova versão de produção
  "build": "next build",
  // Deve ser executado após o build, porque ele é responsável por iniciar a versão de produção
  "start": "next start"
}
```

Crie um diretório chamado `pages` para que o Next se encarregue de transformar cada arquivo dentro da pasta em uma rota.

```js
// pages > Index.js
import React from 'react'

const Index = () => {
  return <h1>Hello World</h1>
}

export default Index
```

Para rodar o component levante o servidor:

```js
npm run dev
```

## Link
A navegação em meio as rotas pode ser otimizada utilizando um componente react:

```js
// pages > index.js
import React from 'react'
import Link from 'next/link'

const Index = () => {
  return (
    <div>
      <h1>Hello World</h1>
      <div>
        <Link href='/sobre'>
          <a>Sobre</a>
        </Link>
      </div>
    </div>
  )
}

export default Index
```

```js
import React from 'react'
import Link from 'next/link'

const Sobre = () => {
  return (
    <div>
      <h1>Sobre</h1>
      <div>
        <Link href='/'>
          <a>Voltar</a>
        </Link>
      </div>
    </div>
  )
}

export default Sobre
```

## SWR
```js
npm install swr
```

O Next.js permite a criação de API facilmente, basta criar uma pasta com o nome `api` dentro da pasta `pages`:

```js
// pages > api > get-text.js
export default async(req, res) => {
    res.end(JSON.stringify({
        showMessage: true,
        message: "Essa é a mensagem"
    }))
}
```

O SWR permite realizar requisições ao servidor toda a vez em que o usuário ativa a tela, ou seja, se a variável `showMessage` for passada para `false` e o site estiver aberto em um cliente que minimizou a tela, assim que ele reabrir a tela uma requisição será disparada para o servidor para atualizar os dados dependentes do `useSWR`.

```js
// index.js
import React from 'react'
import useSWR from 'swr'

const fetcher = (...args) => fetch(...args).then(res => res.json())

const Index = () => {
    const {data, error } = useSWR('/api/get-message', fetcher)
    return (
        <div>
            <h1>Início</h1>
            {!data && <p>Carregando...</p>}
            {!error && data && data.showMessage &&
                <p>{ data.message }</p>
            }
        </div>
    )
}

export default Index
```
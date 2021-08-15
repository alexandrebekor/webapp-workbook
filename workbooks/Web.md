# HyperText Transfer Protocol
É Um conjunto de regras para transferência de textos que são chamados de `hyper` porque podem possuir imagens, vídeos e informações mais complexas.

Esse protocolo permite a troca de informações e dados na internet, para cada solicitação individual de recurso da página temos uma troca de informação individual.

A troca de dados entre o navegador e o servidor pode ser observada de modo macro como:

```
[Browser]   ->    Request    ->  [Servidor]
[Browser]   <-    Response   <-  [Servidor] 
```

# Request
O `Request` carrega uma mensagem que possui:
- Método: que define o tipo de pedido e a ação que será executada no servidor.
> - Get: pega um recurso
> - Post: criar um recurso
> - Patch: atualiza um recurso
> - Put: atualiza um recurso
> - Delete: deleta um recurso

- Headers
- Body

# Response
O `Response`carrega uma mensagem que possui:
- Status Code: um código que corresponde o estado da requisição
- Headers
- Body

# Request/ Response
Apesar de toda mensagem carregar um `Header` e um `Body`, esses são atributos que podem estar vazios.
- Headers: são campos informativos do tipo Chave:Valor
- Body: carrega o conteúdo da requisição

# Conceito
Toda mensagem enviada é `Stateless`, ou seja, não guarda estado, cada nova requisição traz novas respostas, por isso quando precisamos guardar informações entre requisições utilizamos `cookies`, `sessions` ou `storages`.

# Proxies
São todos os componentes que ficam entre o cliente e o servidor, eles colaboram para o transporte da dados.

# URI
Uniform Resource Identifier

É um identificador de recursos que carrega um nome e a localização desse recurso.

Esses parâmetros de nome e localização são identificados como:

- Locator -> URL (Uniform Resource Locator)
  > Toda URL possui um `Protocolo` e um `Domínio` e opcionalmente pode possuir: `subdomínio`, `path`, `parâmetros`, `porta`, `âncora`

- Name -> URN (Uniform Resource Name)

# HTTP Messages
Existem duas versões de HTTP:
- HTTP/1.1: que é um texto legível
- HTTP/2: é a mesma maneira utilizada na versão 1.1 porém com algumas otimizações e a estrutura do texto passou de legível para binária

## Request
A `Request` é composta por:
- Request Line
  - Method
  - Protocol Version
  - URI
- Headers
- Body

## Response
A `Response` é composta por:
- Protocol Version
- Status Code
- Headers
- Status Message
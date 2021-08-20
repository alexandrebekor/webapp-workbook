# Conectar em uma planilha Google

Após realizar o download do arquivo de credenciais, faça a instalação do módulo do Google Spreadsheet no projeto.

```js
npm install google-spreadsheet
```

Adione o email das credenciais como editor na planilha que será acessada.

```js
// index.js
const { GoogleSpreadSheet } = require('google-spreadsheet')
const credentials = require('./credentials.json')

const doc = new GoogleSpreadSheet('id_da_planilha')

const run = async () => {
    await doc.useServiceAccountAuth(credentials)
    await doc.loadInfo()
    console.log(doc.title)
}
run()
```

## Leitura dos Dados
```js
const run = async () => {
    try {
        await doc.useServiceAccountAuth(credentials)
        await doc.loadInfo()
        // console.log(doc.title)

        const sheet = doc.sheetsByIndex[2]
        await sheet.loadCells('A3:C3')
        // console.log(sheet.title)
        const valueCell = sheet.getCell(1, 0)
        // console.log(valueCell.value)
    } catch (err) {
        console.log(err)
    }
}
```
## Escrita de dados
Para inserir dados em uma `sheet` primeiro identifique o cabeçalho na primeira linha, ele servirá de referência para criação do objeto de inserção.

```js
const run = async () => {
    try {
        await doc.useServiceAccountAuth(credentials)
        await doc.loadInfo()
        // console.log(doc.title)

        const sheet = doc.sheetsByIndex[1]
        // Cabeçalho na planilha
        // Nome | Sobrenome | Whatsapp
        await sheet.addRow({
            Nome: 'Alexandre',
            Sobrenome: 'Bekor',
            Whatsapp: '000000000'
        })
    } catch (err) {
        console.log(err)
    }
}
```

> O valor da `key` do objeto deve ser exatamente igual ao escrito no cabeçalho, é possível declarar a key entre aspas caso a descrição seja composta por mais de uma palavra:

```js
await sheet.addTow({
    "Nome Completo:": "Alexandre Bekor"
})
```
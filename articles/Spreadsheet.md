# Conectar em uma planilha Google

Após realizar o download do arquivo de credenciais, faça a instalação do módulo do Google Spreadsheet.

Adione o email das credenciais como editor na planilha que será acessada.

```js
npm install google-spreadsheet
```

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
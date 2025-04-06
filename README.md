<div align="center">
  <img src="docs/assets/logo.svg" alt="logo" height="90" align="center">
  <h1 align="center">telegraf.js</h1>

  <p>Framework moderno da API de Bots do Telegram para Node.js</p>

  <a href="https://core.telegram.org/bots/api">
    <img src="https://img.shields.io/badge/Bot%20API-v7.1-f36caf.svg?style=flat-square" alt="Versão da API do Bot" />
  </a>
  <a href="https://packagephobia.com/result?p=telegraf,node-telegram-bot-api">
    <img src="https://flat.badgen.net/packagephobia/install/telegraf" alt="Tamanho de instalação" />
  </a>
  <a href="https://github.com/telegraf/telegraf">
    <img src="https://img.shields.io/github/languages/top/telegraf/telegraf?style=flat-square&logo=github" alt="Linguagem principal no GitHub" />
  </a>
  <a href="https://telegram.me/TelegrafJSChat">
    <img src="https://img.shields.io/badge/Chat%20em%20Inglês-grey?style=flat-square&logo=telegram" alt="Chat em Inglês" />
  </a>
</div>

## Para usuários da versão 3.x

- [Documentação da v3.x](https://telegraf.js.org/v3)
- [Notas da versão 4.0](https://github.com/telegraf/telegraf/releases/tag/v4.0.0)

## Introdução

Bots são contas especiais do [Telegram](https://telegram.org) criadas para lidar automaticamente com mensagens.
Usuários interagem com bots enviando comandos em chats privados ou em grupos.
Essas contas funcionam como uma interface para código executado no seu servidor.

Telegraf é uma biblioteca que facilita o desenvolvimento de bots do Telegram usando JavaScript ou [TypeScript](https://www.typescriptlang.org/).

### Funcionalidades

- Suporte completo à [API de Bot 7.1 do Telegram](https://core.telegram.org/bots/api)
- Tipagens excelentes para TypeScript
- [Leve](https://packagephobia.com/result?p=telegraf,node-telegram-bot-api)
- Pronto para usar em:
  - [AWS **λ**](https://docs.aws.amazon.com/lambda/latest/dg/nodejs-prog-model-handler.html)
  - [Firebase](https://firebase.google.com/products/functions/)
  - [Glitch](https://glitch.com/edit/#!/dashing-light)
  - [Fly.io](https://fly.io/docs/languages-and-frameworks/node)
  - Entre outros
- Compatível com webhooks `http/https/fastify/Connect.js/express.js`
- Extensível

### Exemplo

```js
const { Telegraf } = require('telegraf')
const { message } = require('telegraf/filters')

const bot = new Telegraf(process.env.BOT_TOKEN)
bot.start((ctx) => ctx.reply('Bem-vindo'))
bot.help((ctx) => ctx.reply('Me envie um sticker'))
bot.on(message('sticker'), (ctx) => ctx.reply('👍'))
bot.hears('oi', (ctx) => ctx.reply('E aí!'))
bot.launch()

// Parada segura
process.once('SIGINT', () => bot.stop('SIGINT'))
process.once('SIGTERM', () => bot.stop('SIGTERM'))

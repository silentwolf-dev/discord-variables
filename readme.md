## discord-variable 

> more events support and documentation coming soon


```js
const { Client, Intents } = require('discord.js')

const { converter } = require("./lib/index")

const intents = new Intents(32767)

const compiler = new converter()


const client = new Client({
    intents: intents,
})

client.on("ready", bot => console.log('ready'))

client.on("messageCreate", message => {
    // logs out username with tag looks something like this foo#8909
    console.log(compiler.parseOnMessage('{user_tag}', message))
})

client.on('guildMemberAdd', member => {
    // mention the user
    console.log(compiler.parseOnJoin('{user}', member))
})

client.login("your token")
```

## variables

| variable       | Description                                           |
| -------------- | ------------------------------------------------------|
| {user}         | @mention the user                                     |
| {user_tag}     | `foo#5678`                                            |
| {username}     | The `username` of the user                            |
| {user_discrim} | placeholder for the user tag  `5689`                  |
| {user_id}      | placeholder for the user id                           |
| {user_avatar}  | placeholder for the user avatar                       |
| {user_nick}    | the user nickname works better with on `parseOnJoin()`|
| {user_createdAt}| createdAt in a readable date and time `M/D/Y h:m`    |
| {server_icon}  | placeholder for the server icon returns the server icon|
| {server_id}    | the server id                                          |
| {server_owner} | `@mention` the server owner                              |
| server_owner_id} |  the server owner id 

-------------------------------------------more coming soon--------------------------------
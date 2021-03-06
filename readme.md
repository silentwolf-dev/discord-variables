## discord-variable 

> more events support coming soon




# example

```js
client.on("messageCreate", message => {
    // You can also get your data from a database
    const parser = new converter("You have {user_bal} in your wallet and {user_bank} in your", {
        bank: 100,
        balance: 200,
    })


    console.log(parser.parseOnMessage(message))
    // output: You have 200 in your wallet
})
```

## converter class Options

> the `converter class` option object, The object allow to set bank and balance value to whatever You want and which will allow You to use `{user_bal}` and `{user_bank}` by default `{user_bal}` and `{user_bank}` is equal __0__`.


## converter.getVariables()

> `converter.getVariables()` return an Array of Objects containing all the variables



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
| {server_owner} | `@mention` the server owner                            |
|{server_name}   | placeholder for the server name
|server_owner_id} |  the server owner id 
|{server_memberCount} | the amount of members in the server  |
|{channel_id}    | return the channel id this only works on ` parseOnMessage`|
| {server_name} | return the server name  |
| {user_bal}    | return the user balance |
| {user_bank}   | return the user bank |

# methods


|           Title              |                Description               |
|------------------------------|------------------------------------------|
|      ` converter `           |The conveter class take string and a Option parameters|
| `parseOnJoin()` | Parse text in the `guildMemberAdd` Event and need the member parameter __in order to work__|
| `parseOnMessage` | Parse text in the `messageCreate` Event and need the message parameter __in order to work__|
| `parseOnMemberRemove` | Parse text in the `guildMemberRemove` Event and need the member parameter __in order to work__| 
| `getVariables`  | return a string array of all the variables            |


## converter.parseOnJoin()

> `coverter.parseOnJoin()` parse message in the `guildMemberAdd` event and take member as its first `paramater`, and take the text that is being parsed as its last `paramater`.

```js
client.on("guildMemberAdd",  member => {
  const parser = new converter()
  
  console.log(parser.parseOnJoin(member, "welcome {user} to {server_name}"))

  // for the above example output: welcome @foo to discord-variable

})
```
## converter.parseOnMessage()
> `converter.parseOnMessage()` parse message in the `messageCreate` event and take message as its first `paramater`, and take the text that is being parsed as its last `paramater`.


```js
client.on("messageCreate", message => {
  const parser = new converter()
  
  console.log(parser.parseOnMessage(message, "welcome {user} to {server_name}"))

  // for the above example output: welcome @foo to discord-variable

})
```
## converter.parseOnMemberRemove()
> `converter.parseOnMemberRemove()` parse message in the `guildMemberRemove` event and take member as its first `paramater`, and take the text that is being parsed as its last `paramater`.

```js
client.on("guildMemberRemove",  member => {
  const parser = new converter()
  
  console.log(parser.parseOnMemberRemove(member, "goodbye {user} from {server_name}"))

  // for the above example output: goodbye @foo from discord-variable
})
```




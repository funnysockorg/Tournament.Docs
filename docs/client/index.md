# Client

* Пользователь заходит на сайт, где ему объясняют, зачем этот сайт предназначен, и предлагают войти через [Discord OAuth2](https://discord.com/developers/docs/topics/oauth2)
* Пользователь нажимает войти, и его перекидывает на [авторизацию Discord'а](https://discord.com/oauth2/authorize)
* Пользователь соглашается, и Discord перекидывает его обратно на сайт, где ему показывают две гифки, одну из которых нужно выбрать
* Пользователь выбирает гифку, и программа дает ему следующую пару гифок
* Так продолжается до тех пор, пока не закончится сравнение двух гифок. После этого пользователю показывается список гифок от самой лучшей до худшей и кнопка "Отправить результат"

```mermaid
sequenceDiagram
  actor user
  participant client
  participant server

  user->>+server: войти
  server->>-client: index.html

  alt в кэше входил?
    server->>user: впустить


  else
    client->>user: добавить кнопку "войти"
    server->>user: зарегистрироваться

  end

  %% авторизоваться
```

```mermaid
sequenceDiagram
  participant Client as Client
  participant Discord as Discord
  participant Server as Server

  Client->>+Discord: GET api/oauth2/authorize
  Discord-->>+Client: Redirect api/auth/sign?code=...
  Client->>+Server: GET api/auth/sign?code=...
  Server->>+Discord: POST api/oauth2/token { code: ...#59; client_secret: ... }
  Discord-->>+Server: { access_token: 1#59; refresh_token: 2 }
  Server-->>+Client: { access_token: 1#59; refresh_token: 2 }
```

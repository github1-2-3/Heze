# Heze

Heze is a light Swift server-side framework powered by Perfect 3.x.

# Get started

Heze recommends MySQL 5.7.

## Install

- Make sure you have `mysql server 5.7` installed on your Mac.
- Clone this repo.
- Fill `username` and `password` field in config file at `Workspace/HezeDemo/config.json`.
- Run `swift package generate-xcodeproj` to generate the Xcode project.
- Edit path params in `main.swift` at `HezeDemo`.
- RUN. Go to `http://localhost:8080` to see how the demo looks.

## View rendering

- API: Use `HezeHandler` to process request and return a JSON object by using `HezeResponse` method.
- Web: Use `HezeView` or `HezeListView`. HTML rendering uses `Mustache` tech which is powered by [Perfect-Mustache](https://github.com/PerfectlySoft/Perfect-Mustache)

Routes need to be registered in AppDelegate. See the demo.

## Filter

- Request filter: Use `HezeRequestFilter`. Override `requestFilter` method to decide if the request can pass the filter.
- Response filter: Use `HezeResponseFilter`.
- Session: `HezeSessionRequestFilter` is a request filter to process session. Tokens are stored in MySQL by default.

Filter need to be registered in AppDelegate as a plugin.

## Timer

Use `HezeTimer`.

Timer need to be registered in AppDelegate as a plugin.

## Workspace

Workspace contains:

- `config.json`: Configration.
- `Public`: Static resources.
- `Views`: Web templates.

## Context

Context system allows you to create multiple servers in one target. 

Every AppDelegate requires a context. `HezeApp` will storage some env vars in this context when it inits.

There are main context and meta context by default. You can create more context. See `HezeContextBox`.

DO NOT TOUCH META CONTEXT.

## Email

Heze supports email.

Adding these config in `config.json` will enable the email client.

```json
"mail": {
    "smtp": "smtp://xxx",
    "username": "noreply@xxx",
    "password": "",
    "name": "xxx-NoReply",
    "interval": 3.0,
}
```

It's powered by [PerfectSMTP](https://github.com/PerfectlySoft/Perfect-SMTP).

## Need other database?

Look at class `HezeDatabase`. It's a abstract interface of database. Feel free to implement `HezeDatabaseImpl` yourself.

You may need to process Session yourself because `HezeSessionRequestFilter` is powered by [PerfectSessionMySQL](https://github.com/PerfectlySoft/Perfect-Session-MySQL).

# Preview

My website [https://blog.yuusann.com](https://blog.yuusann.com) is powered by Heze and SPiCa.

SPiCa is another framework which is used to create Vue app using Swift. Not opensource yet.

# Question?

Feel free to contact me: [i@yuusann.com](mailto:i@yuusann.com)
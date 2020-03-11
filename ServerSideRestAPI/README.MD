# Introduction
This is the mechanism that will handle requests from the front end GUI and interact with the Data Store.

Initially, the service endpoints will be defined in a Swagger definitions file and used to generate GOLANG code stubs for development.  However, other RESTful service definitions are possible and other programming languages could be used instead.

Initially, this is the target component for learning.  The setup will be left incomplete for the learning developer to fill in here.

# Developer Setup

## Prerequsites
* GIT: https://git-scm.com/book/en/v2/Getting-Started-Installing-Git
* Go-Swagger: https://goswagger.io/install.html

## Initial Setup

Go-ElasticSearch is provided for you in this configuration.  It is a Git Submodule.  In order to initialize it, run the following commands:

```
git submodule init
git submodule update
```

# TASKING INSTRUCTIONS

In the subdirectory ./rest-server/hero-server/, you will see a directory called swagger.  This is an initial layout just like Go-Swagger's Custom Server tutorial.

1. Generate the server code using the swagger tool.
  a. Warning: the generated go code may fail to execute if the code is generated with sudo and belongs to the `root` user.  To fix this, run the command `sudo chown -R ${USER}:${USER} ./gen` (chown changes ownership,  ${USER} should use the currently logged in user, -R make it a recursive operation)
2. Implement all the necessary functions.

## CAUTIONS

1. As mentioned above, the `swagger generate` command may generate code you cannot execute.  This is typically because the generated code belongs to `root`, not your user account.  Use `chown` to fix this.

2. PORT: By default, the go-swagger tool does not generate a port for you to use.  You will need to specify one.  If you do not specify a port or you specify one other than `:3000`, then you will need to update the Front End GUI's hero.service.ts.

3. CORS: You will probably run into Cross Origin errors.  This is a security feature implemented in all modern browsers.  To bypass this issue, you will need to make specific changes to your Go Middleware.Responder.
  a. Find this function in your generated code: `func setupGlobalMiddleware(handler http.Handler) http.Handler`
  b. Replace its contents with the following:
    ```
    func setupGlobalMiddleware(handler http.Handler) http.Handler {
        corsHandler := cors.New(cors.Options{
            Debug:          false,
            AllowedHeaders: []string{"*"},
            AllowedOrigins: []string{"*"},
            AllowedMethods: []string{},
            MaxAge:         1000,
        })
        return corsHandler.Handler(handler)
    }
    ```
  c. Add this import to the file: `"github.com/rs/cors"`
  d. Rerun the `go get` import downloader command.
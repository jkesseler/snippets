# How to handle application configuration

In short: [Use environment variables](https://12factor.net/config)

Application config is everything that is likely to change between deploys. This
includes things like database credentials, hostnames, etc. It does not includes
application specific configuration like routes since that does not change between deploys.

There has to be a strict separation between application code and it's
configuration. Code does not change, config does. Therefore configuration should
never be defined in code with the risk off adding sensitive data the repository.

For NodeJS based environments you can use the [dotenv](https://www.npmjs.com/package/dotenv) package.

# Package Json
use to setup project
## Automate command
use case suppose we need to create clean up script for dev enviroment
```
script: {
    "db:dev:rem": "docker compose rm dev-db -s -v -f",
    "db:dev:up": "docker compose up dev-db",
    "db:dev:restart": "yarn db:dev:rem & yarn db:dev:up"
}
```
running in terminal
```
yarn db:dev:restart
```

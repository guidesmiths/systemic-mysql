# systemic-mysql
A [systemic](https://github.com/guidesmiths/systemic) Mysql component

## Usage
```js
const System = require('systemic')
const mysql = require('systemic-mysql')

new System()
    .configure({
        mysql: {
          connectionLimit: config.ConnectionLimit,
          host: config.host,
          user: config.user,
          password: config.password,
          database: config.database,
        }
    })
    .add('logger', console)
    .add('mysql', mysql()).dependsOn('config', 'logger')
    .start((err, components) => {
        // Do stuff with components.pg
    })
```

## Ensure Dependencies

In order to run the tests a mysql server is required. A fake docker server can be created easily with docker.

```
docker run --name mysql \
  -e MYSQL_USER=admin -e MYSQL_PASSWORD=password -e MYSQL_DATABASE=example -e MYSQL_ROOT_PASSWORD=123456 \
  -p 3306:3306 -d mysql/mysql-server:5.7
```

1: yarn create strapi-app srapsware-strapi-admin

2: yarn add @strapi/utils

3: add to ignore

.editorconfig
.env.example
.eslintrc
.strapi*
.eslintignore
yarn.lock
jsconfig.json

4: yarn add pg

5: add to .env

DATABASE_URL=${{Postgres.DATABASE_URL}}
PGDATABASE=${{Postgres.PGDATABASE}}
PGHOST=${{Postgres.PGHOST}}
PGPASSWORD=${{Postgres.PGPASSWORD}}
PGPORT=${{Postgres.PGPORT}}
PGUSER=${{Postgres.PGUSER}}

6: create production database config file

config/env/production/database.js

module.exports = ({ env }) => ({
  connection: {
    client: 'postgres',
    connection: {
      host: env('PGHOST', '127.0.0.1'),
      port: env.int('PGPORT', 5432),
      database: env('PGDATABASE', 'strapi'),
      user: env('PGUSER', 'strapi'),
      password: env('PGPASSWORD', 'password'),
      ssl: env.bool(true),
    },
    pool: { min: 0 }
  },
});
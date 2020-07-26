# Speckle Server

The next iteration of the Speckle Server.

[![Speckle-Next](https://circleci.com/gh/Speckle-Next/SpeckleServer.svg?style=svg&circle-token=76eabd350ea243575cbb258b746ed3f471f7ac29)](https://github.com/Speckle-Next/SpeckleServer/) [![codecov](https://codecov.io/gh/Speckle-Next/SpeckleServer/branch/master/graph/badge.svg?token=PHZWVNUVFE)](https://codecov.io/gh/Speckle-Next/SpeckleServer)


## Contributing

### Local debugging & testing

To debug, simply run `npm run dev:server`. To test, run `npm run test:server`. To run tests in interactive mode, run `npm run test:server:watch`.

#### Requirements

1. Duplicate and rename `.env-example` to `.env`.

2. You will need to have a postgres instance running on the default settings, with two databases present, named `speckle2_dev` and `speckle2_test`.

> For getting postgres running on osx, check out [postgres.app](https://postgresapp.com/), and the classic [pgadmin](https://www.pgadmin.org/download/pgadmin-4-macos/).

3. You will also need Redis installed.

> For which you can use the [redis.app](https://jpadilla.github.io/redisapp/).

### How to commit to this repo
When pushing commits to this repo, please follow the following guidelines:

- Install [commitizen](https://www.npmjs.com/package/commitizen#commitizen-for-contributors) globally (`npm i -g commitizen`).
- When ready to commit, type in the commandline `git cz` & follow the prompts.

## Modules

The server dynamically loads individual 'modules' from each top level folder in `./modules`. It first loads the core modules, and thereafter others.

Modules can create new and alter old database tables, if the knex migration files are present in a `migrations` subfolder (e.g., `./modules/your-module/migrations/my-new-table.js`). Make sure to add a date in front of your migration file.

### Structure

A module should contain in its root folder an index.js file that exposes an init function:

```js
exports.init = ( app ) => {
    // Your module's initialisation code
}
```

Any database migration files should be stored and named accordingly in a `migrations` folder. Moreover, modules should include test files. These should be located in `tests`. Here's a sample structure:

```

|-- index.js // entry file
|-- migrations
    `-- myTable.js
`-- tests
    `-- example.spec.js

```

// TODO

## API

### GraphQl

// TODO
### REST

Depecrated.


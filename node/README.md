# Docker-Compose Examples for Node Development

## Prerequisites

1. [Install Docker](https://www.docker.com/).

## Usage

### Install or update NPM or Bower packages

Every time the `package.json` or `bower.json` is updated, re-build the containers:

```
docker-compose build
```

### Start the app

```
docker-compose up app
```

### Run tests

```
docker-compose run --rm test npm test
```

### Run other Node/NPM/Bower commands or scripts

```
docker-compose run --rm app node …
docker-compose run --rm app npm …
docker-compose run --rm app bower …
```

### Run watch

```
docker-compose up test
```

To verify `watch` is running, make a minor change to `test/test.js`, save it, then watch the console for test output.

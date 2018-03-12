# Docker-Compose Examples for Rails Development

## Prerequisites

1. [Install Docker](https://www.docker.com/).
1. Optional: [Install Guard](https://github.com/guard/guard#installation), using `docker-compose run --rm test bundle exec guard init` to generate an empty `Guardfile`.

## Usage

### Install or update gems

Every time the `Gemfile` is updated, re-build the containers:

```
docker-compose build
```

### Start the app

Three-step process that allows you to interact with `binding.pry`:

```
docker-compose up -d app
docker attach my-rails-app
```

Now you should be able to see the app running locally at http://localhost:3000/.

### Run tests

To run the entire test suite:

```
docker-compose run --rm test bundle exec rspec
```

To run a single test file:

```
docker-compose run --rm test bundle exec rspec spec/unit/model_spec.rb
```

To run a single example in a single test file:

```
docker-compose run --rm test bundle exec rspec spec/unit/model_spec.rb -e 'some string or substring of the example you want to run'
```

**OR**

```
docker-compose run --rm test bundle exec rspec spec/unit/model_spec.rb:{LINE NUMBER}
```

### Use the Rails console

```
docker-compose run --rm app bin/rails console
```

### Run Rake tasks

```
docker-compose run --rm app bundle exec rake …
```

### Guard

```
docker-compose up -d test
docker attach my-rails-test
```

To verify guard is running, make a minor change to a test, save it, then watch the console for test output.

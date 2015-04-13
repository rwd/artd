# Europeana Annotations Round-tripping daemon (ARTd)

## License

Licensed under the EUPL V.1.1.

For full details, see [LICENSE.md](LICENSE.md).

## Requirements

* Ruby 2.2.1
* MySQL database

## Installation

* Download the source code
* Run `bundle install`

## Configuration

### Environment variables

Most configuration settings are read from environment variables, described in
detail below.

In development and test environments, these can be placed in a 
[.env](https://github.com/bkeepers/dotenv) file in your application root.

#### SECRET_KEY_BASE

Your secret key is used for verifying the integrity of signed cookies.
If you change this key, all old signed cookies will become invalid!

Make sure the secret is at least 30 characters and all random,
no regular words or you'll be exposed to dictionary attacks.
You can use `bundle exec rake secret` to generate a secure secret key.

#### PORT

This sets the TCP port on which the Puma web server will listen for HTTP
connections. If unset, it will default to 3000.

#### RACK_ENV

The application environment to run, i.e. development, test or production.
Defaults to development.

#### WEB_CONCURRENCY

The number of Puma workers to run. Defaults to 2.

#### MAX_THREADS

The number of threads to run per Puma worker. Defaults to 5.

### Database

1. Create a MySQL database, and configure in config/database.yml (see
  http://guides.rubyonrails.org/configuring.html#configuring-a-database)
2. Initialize the database: `bundle exec rake db:setup`

## Usage

Run the app with the Puma web server: `bundle exec puma -C config/puma.rb`

By default, Puma will listen on the port defined in the `PORT` environment
variable, or 3000 by default.

# Postgres Jupyter Environment

Using docker compose, we provide an easy method of connecting jupyter to an
isolated postgresql database. This can be an effective way of exploring
existing relational data.

## Usage

    docker-compose up

Following the above, jupyter lab will be running on port 8888. Through
jupyter lab, you may use the sqlalchemy library to connect to postgres
at the hostname "postgres".

The postgres database starts off empty. See below for instructions on how to
populate it with data.

## Populating postgres

TODO
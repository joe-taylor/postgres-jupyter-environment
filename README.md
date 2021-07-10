# Postgres Jupyter Environment

Using docker compose, we provide an easy method of connecting jupyter to an
isolated postgresql database. This can be an effective way of exploring
existing relational data.

## Usage

    docker-compose up

After entering the above in your terminal of choice, Jupyter Lab will start
listening on port 8888. Visit http://localhost:8888 to access Jupyter Lab,
and then in a new notebook, use the sqlalchemy library to connect to
postgres. Postgres is available in the docker-compose created private
network (which your notebook has access to) using the hostname "postgres".
See example notebook for more details.

The postgres database starts off empty. See below for instructions on how to
populate it with data from a postgres dump.

## Populating postgres from preexisting dump

TODO
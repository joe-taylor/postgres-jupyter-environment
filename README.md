# Postgres Jupyter Environment

This project uses Docker Compose to provide a preconfigured Jupyter notebook
connected to an isolated postgresql database. This is an effective method of
exploring relational data.

## Usage

    docker-compose up

After entering the above in your terminal of choice, Jupyter Lab will start
listening on port 8888. Use the link provided in the Docker Compose output
(e.g.,
http://127.0.0.1:8888/lab?token=4837417482e1dc7f3ff5c47cd0cbb71bdffff85e041ab74f)
to access Jupyter Lab, and then in a new notebook, use the sqlalchemy library
to connect to postgres. Postgres is available in the private network Docker
Compose creates for you under the hostname "postgres". Your notebook will
have access to this hostname by default; no further configuration is
required. Additionally, the ipython-sql magic is loaded and connected already
so you can run queries with %sql right away. See example notebook for more
details.

The postgres database starts off empty. See below for instructions on how to
populate it with data from a postgres dump.

## Populating postgres from preexisting dump

To clear and recreate necessary users and databases:

    docker-compose exec postgres dropuser -U postgres USERNAMEHERE
    docker-compose exec postgres createuser -U postgres USERNAMEHERE
    docker-compose exec postgres dropdb -U postgres DBNAMEHERE
    docker-compose exec postgres createdb -U postgres DBNAMEHERE

To dump to a file on your local disk:

    export DATABASE_TO_DUMP=foo
    docker-compose exec postgres pg_dump -Fc -U postgres $DATABASE_TO_DUMP  > /path/to/db.dump

To restore from database dump, clear and recreate any necessary users and databases, and then run the following:

    cat /path/to/db.dump | docker-compose exec -T postgres pg_restore -U postgres -d postgres

## References

 - [PostGIS Book](https://postgis.gishub.org/chapters/installation.html)
 - [datacamp: SQL Interface within JupyterLab](https://www.datacamp.com/community/tutorials/sql-interface-within-jupyterlab)

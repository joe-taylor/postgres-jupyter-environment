# Postgres Jupyter Environment

This project uses Docker Compose to provide a preconfigured Jupyter notebook
connected to an isolated postgresql database. This can be an effective way to
explore relational data.

## Usage

    docker-compose up

After entering the above in your terminal of choice, Jupyter Lab will start
listening on port 8888. Use the link provided in the Docker Compose output
(e.g., http://127.0.0.1:8888/lab?token=4837417482e1dc7f3ff5c47cd0cbb71bdffff85e041ab74f) to access Jupyter Lab,
and then in a new notebook, use the sqlalchemy library to connect to
postgres. Postgres is available in the default private network Docker Compose
creates for you, using the hostname "postgres". Your notebook will have
access to this hostname by default; no further configuration is required. See
example notebook for more details.

The postgres database starts off empty. See below for instructions on how to
populate it with data from a postgres dump.

## Populating postgres from preexisting dump

TODO

## References

 - [PostGIS Book](https://postgis.gishub.org/chapters/installation.html)
 - [datacamp: SQL Interface within JupyterLab](https://www.datacamp.com/community/tutorials/sql-interface-within-jupyterlab)
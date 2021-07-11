FROM debian:buster
RUN apt-get update && \
    apt-get -y install python3-pip libpq-dev && \
    rm -rf /var/lib/apt/lists/*
RUN useradd -ms /bin/bash jupyter
USER jupyter
RUN pip3 install ipython-sql psycopg2 sqlalchemy jupyterlab pandas numpy
ENV PATH=/home/jupyter/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/lib/postgresql/9.6/bin
WORKDIR /home/jupyter/
COPY ./Example.ipynb Example.ipynb
COPY ./ipython-sql-startup.py /home/jupyter/.ipython/profile_default/startup/ipython-sql.py
USER root
RUN chown jupyter:jupyter ./Example.ipynb
RUN chown -R jupyter:jupyter /home/jupyter/.ipython
USER jupyter
CMD ["jupyter", "lab", "--ip=0.0.0.0"]
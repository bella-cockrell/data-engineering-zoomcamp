# Week 1 notes

## Start up

Create a Dockerfile and, in the directory, run 

```bash
docker build -t test:pandas .
```

This will build the image into a container, give it a tag of `test:pandas` and specify to use the Dockerfile in the current directory.

Then run:
```bash
docker run -it test:pandas 2021-02-10
```

This will run the tagged container called `test:pandas` interactively (i.e. will drop you into the container) with the argument of `2021-02-10`.

## Postgres

To run a Postgres container with an attached volume, first create a directory called `ny_taxi_postgres_data`. Then run:
```bash
docker run -it -e POSTGRES_USER="root" -e POSTGRES_PASSWORD="root" -e POSTGRES_DB="ny_taxi" -v $(pwd)/ny_taxi_postgres_data:/var/lib/postgresql/data -p 5432:5432 postgres:13
```
NOTE: 
Run `docker ps` to see what containers are currently running if you get a port issue.

When your Python env is set up (see [pyenv virtualenv](https://github.com/pyenv/pyenv-virtualenv) for more info), install Postgres with
```bash
brew install postgresql
```
and then 
```bash
pip install pgcli
```
Run `pgcli --help` to see if it is working. Then, assuming you already have the container running, run
```bash
pgcli -h localhost -p 5432 -u root -d ny_taxi
```
And then enter in your password for the container (see above).

Run a basic Postgres command (like `\dt` to list the tables) to see if it is working.

## Jupyter
Jupyter is an interactive environment for Python (PyCharm is another such environment).

```bash
pip install jupyter
```

To start it, run `jupyter notebook` in the terminal. It will open up a browser window for you.

## NY Taxi Data
The link for the data can be found [here](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page).
 
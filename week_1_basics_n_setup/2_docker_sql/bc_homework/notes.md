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


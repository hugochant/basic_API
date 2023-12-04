# Basics to build an API
This repository explain the basics to build your first api.

You can use the structure of the repository.

The API is build with  [Fastapi](https://fastapi.tiangolo.com/fr/, "Fastapi") and [Uvicorn](https://www.uvicorn.org/, "Uvicorn").

To start run `pip install -r requirements.txt` and install [docker desktop](https://docs.docker.com/desktop/).


## API

To check if everything is good run the `uvicorn app_folder.app_file:app --host 0.0.0.0` in your terminal.

If the prévious step is good you can build your docker in local with the following command `docker build -t name_of_your_api .`.

To run it you have to run the command `docker run -p 8080:8000 name_of_your_api`.

If everything is good here you can access to your API [here](http://localhost:8080/).

To test your API you can check every endpoint here [local](http://localhost:8080/docs).

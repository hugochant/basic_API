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

## Deploy on GCP

Now everything is running localy we have to deploy it.

First thing is to create a gcp account if you don't have one yet. 

When it's done you have to activate [google artifact](https://console.cloud.google.com/artifacts?) if it's not.

Check if everything is up to set with your installation `gcloud components update`.

You have to create a new repository on google artifact for your images. We do it by running this following command: 
`gcloud artifacts repositories create $REPOSITORYNAME \
    --repository-format=docker \
    --location=$LOCATION \
    --description="Repository for storing api images"`.

If the command runs without error you can see your repository [here](https://console.cloud.google.com/artifacts?).

Let's build the image for prod `docker build -t  $GCP_REGION-docker.pkg.dev/$GCP_PROJECT/$ARTIFACT_REPOSITORY/$IMAGE_NAME:prod .`.

You can check that your image by running `docker run -e PORT=8000 -p 8000:8000 --env-file .env $GCP_REGION-docker.pkg.dev/$GCP_PROJECT/$ARTIFACT_REPOSITORY/$IMAGE_NAME:prod`: http://localhost:8000/ .

If everything works fine you can now push your image to Google Artifact Registry `docker push $GCP_REGION-docker.pkg.dev/$GCP_PROJECT/$ARTIFACT_REPOSITORY/$IMAGE_NAME:prod`







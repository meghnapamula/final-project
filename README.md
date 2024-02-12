# Dockerizing Flask with Postgres, Gunicorn, and Nginx

In this project, I created a web app that allows users to upload images and gifs from their local computer. The user can then view the image on their browser.

To upload the file, I navigated to this page on my browser: http://localhost:6001/upload

Once file is uploaded, I navigated to this page to view the uploaded file: http://localhost:6001/media/gif-for-big-data.gif

I used the following tutorial: https://testdriven.io/blog/dockerizing-flask-with-postgres-gunicorn-and-nginx/
I used the following README file to build my README file: https://github.com/testdrivenio/flask-on-docker/blob/main/README.md



### Demo

Here is a short gif of me uploading a file at http://localhost:6001/upload, and then viewing said file at http://localhost:6001/media/gif-for-big-data.gif. This gif is of poor quality so I have also uploaded it in video format directly underneath.

![SPLIT CLIP BIG DATA](https://github.com/meghnapamula/flask-on-docker/assets/123199060/e47af095-2953-4386-b452-65b237b1584e)

https://github.com/meghnapamula/flask-on-docker/assets/123199060/4f63d8a3-899e-4a92-bb65-90b5b8a6aab0


### Build Instruction:

Uses the default Flask development server


1. Rename .env.dev-sample to .env.dev
2. Update the environment variables in the docker-compose.yml and .env.dev files
3. Build the images and run the containers:

```
$ docker-compose up -d --build
```

Test it out at http://localhost:6001

### Production
Uses gunicorn + nginx

1. Rename .env.prod-sample to .env.prod and .env.prod.db-sample to .env.prod.db. Update the environment variables.
2. Build the images and run the container:

```
$ docker-compose -f docker-compose.prod.yml up -d --build
$ docker-compose -f docker-compose.prod.yml exec web python manage.py create_db
```

Test it out at http://localhost:6001/upload

No mounted folders. To apply changes, the image must be re-built.

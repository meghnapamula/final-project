# Dockerizing Flask with Postgres, Gunicorn, and Nginx

In this project, I created a web app that allows users to upload images of PNG and JPG formats from anywhere on their local computer. The user can then view the image on the browser.

To upload the file, navigate to this page on your browser: http://localhost:6001/upload

Once file is uploaded, navigate to this page to view uploaded file: http://localhost:6001/media/IMAGE_FILE_NAME


### Demo

(https://github.com/meghnapamula/flask-on-docker/assets/123199060/556e2132-d447-4f2e-9da0-7ac49c798cca)


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

# Heroku

## heroku CLI

## Commands

```sh

# logs
heroku logs --app djb1 --tail

# run
heroku run -a djb1 "python src/manage.py migrate"
heroku run -a djb1 "gunicorn --pythonpath src djpro.wsgi --log-file -"
```


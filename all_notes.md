create:
  requirements.txt
  .dockerignore
  .gitignore
  Dockerfile
  run command "docker build ."

create:
  docker-compose.yml 
  and run command "docker compose build"

create:
  requirements.dev.txt
    .flake8 file under app directory
    add this to docker-compose.yml:
      args:
          - DEV=true
    update Dockerfile
    run command docker compose run --rm app sh -c "flake8"

create django project:
  run docker compose run --rm app sh -c "django-admin startproject app ."
  add this to settings.py:
    ALLOWED_HOSTS = ['0.0.0.0', 'localhost', '127.0.0.1']
  to run django project:
    run docker compose up

  configure github actions:
    create:
      dockerhub Personal access token (username and secret)
      add them to github repository secrets
      add checks.yml under .github/workflows directory
      push code to github and check actions running

create test driven development:
  create sample file eg calc.py
  create test.py and write code to test methods from calc.py
  run docker compose run --rm app sh -c "python manage.py test"

create super user:
  docker compose run --rm app sh -c "python manage.py createsuperuser"

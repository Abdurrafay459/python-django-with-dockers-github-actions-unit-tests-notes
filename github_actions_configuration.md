Github Actions:
  used for:
    Deployment
    Code Linting
    Unit Tests

Trigger(Push to github)  ->  Job(Run Unit Test)  ->  Result(Success/Fail)

**CONFIGURATION**
create .github folder in ROOT FOLDER of the project 
  then create workflows folder inside .github
    then create checks.yml file inside it

**checks.yml**:
---
name: Checks

on: [push]

jobs:
  test-lint:
    name: Test and Lint
    runs-on: ubuntu-20.04
    steps:
      - name: Login to Docker hub
        uses: docker/login-action@v2
        with:
          username: ${{ secrets.DOCKERHUB_USERNAME }}
          password: ${{ secrets.DOCKERHUB_TOKEN }}
      - name: Checkout code
        uses: actions/checkout@v2
      - name: Test
        run: docker compose run --rm app sh -c "python manage.py test"
      - name: Lint
        run: docker compose run --rm app sh -c "flake8"
      

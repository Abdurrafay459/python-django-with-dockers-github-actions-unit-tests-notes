make migrations: 
  python manage.py makemigrations

apply migrations: 
  python manage.py migrate

best practice:
  run it after wait_for_db command, so that every time the app starts, it migrates any changes in the DB

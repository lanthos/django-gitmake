# django-gitmake
Custom Django management command for automatically adding new migration files to git.  More times than I would like I, or someone else on the team, has forgotten to add the migration to git causing issues when pushing.  This was created to help avoid that.  The gitmake.py version is compatible with Django 1.11 and gitmake2.py is compatible with Django 2.2.

## Setup

For full details on custom management commands check out https://docs.djangoproject.com/en/dev/howto/custom-management-commands/

For the tl;dr version:

Copy the management directy and everything below it into an app folder in your Django project (I happened to use core) and test that everythign looks good by running: `python manage.py help`
  
You should see the gitmake command inside of the block for your app.


## Usage

Works exactly like makemigrations except that when it writes the files it will attempt to run `git add <migration>`.  If it experiences an error it will let you know what it was and warn you that you'll have to add it manually.

`python manage.py gitmake --dry-run`  # won't add to git since no files are written


`python manage.py gitmake`  # will add to git since you will have files!  Assuming no errors elsewhere.  Only tries after writing the migration file.

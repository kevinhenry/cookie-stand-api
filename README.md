# Lab 34 - Back End Deployment

Deployed on: [Link](http://35.165.23.133:8000/api/v1/cookie_stands/)

PR: [Link](https://github.com/kevinhenry/cookie-stand-api/pull/3)

Collaboration: Tony Regalado, Anthony Williams

## Overview

It’s time to deploy!

First steps are to make sure your Application is able to run well in a remote environment.

Once you are confident that your Application is *deployable` then time to research deployment options.

## Feature Tasks and Requirements

[x] Use API Quick Start Template
[x] Create a new repo `cookie-stand-api` that uses [API Quick Start](https://github.com/codefellows/python-401-api-quickstart) as a template.
[x] Modify your application using instructions in README.md found in root of repo.
  [x] Change `things` app folder to be `cookie_stands`
  [x] Go through code base looking for `Thing`,`thing` and `things` change to cookie-stand related names.
  [x] E.g. `Thing` model becomes `CookieStand`
  [x] E.g. `ThingList` becomes `CookieStandList`

[x] Pro Tip: Do a global text search looking for `thing`
  [x] Search should be case insensitive.

### Deeper CookieStand Changes

The `CookieStand` model must contain

```location = models.CharField(max_length=256)
owner = models.ForeignKey(
  get_user_model(), on_delete=models.CASCADE, null=True, blank=True)
description = models.TextField(default="", null=True, blank=True)
hourly_sales = models.JSONField(default=list, blank=True)
minimum_customers_per_hour = models.IntegerField(default=0)
maximum_customers_per_hour = models.IntegerField(default=0)
average_cookies_per_sale = models.FloatField(default=0)```

Notice the use of [JSONField](https://docs.djangoproject.com/en/3.1/ref/models/fields/#jsonfield) which is a newer feature introduced in Django 3.1.

### Database Deployment Requirements
[x] Host your Database at ElephantSQL

### Site Deployment Requirements
[x] Deploy Docker container to Heroku -- ?AWS?

### Stretch Goals
[] Add functionality so that when a JSON array of hourly_sales is not provided at creation time it will be generated with random numbers based on minimum/maximum customers per hour and average cookies per sale.
[x] Deploy site with alternate provider. E.g. Digital Ocean, Azure or AWS.

### Implementation Notes
[x] Site must use environment variables.

### Useful Terminal Commands
`docker-compose up --build`
`docker-compose down`
`docker-compose restart`
`docker-compose run web python manage.py migrate`
`docker-compose run web python manage.py collectstatic`

### User Acceptance Tests
[x] Manually confirm API using API Tester, Postman or HTTPie.
  [x] Remember to use deployed url, not localhost

### Getting Started
Clone this repository to your local machine.

$ git clone Link Once downloaded, activate your virtual environment and run by ____________

poetry init poetry shell

####
Template Project for starting up CRUD API with Django Rest Framework

## Customization Steps

- DO NOT migrate yet
- add additional dependencies as needed
  - Re-export requirements.txt as needed
- change `things` folder to the app name of your choice
- Search through entire code base for `Thing`,`Things` and `things` to modify code to use your resource
  - `project/settings.py`
  - `project/urls.py`
  - App's files
    - `views.py`
    - `urls.py`
    - `admin.py`
    - `serializers.py`
    - `permissions.py`
- Update ThingModel with fields you need
  - Make sure to update other modules that would be affected by Model customizations. E.g. serializers, tests, etc.
- Rename `project/.env.sample` to `.env` and update as needed
- Run makemigrations and migrate commands
- Optional: Update `api_tester.py`
####

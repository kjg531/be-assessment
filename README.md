# MetaverseHQ Backend Assessment

[![Built with Cookiecutter Django](https://img.shields.io/badge/built%20with-Cookiecutter%20Django-ff69b4.svg?logo=cookiecutter)](https://github.com/cookiecutter/cookiecutter-django/)

This assessment will be have 3 parts:

- Task Scheduling
- Models
- API

## Task Scheduling

- To get price data please create a free account at https://etherscan.io/apis
- Using docs find correct api endpoint to fetch latest eth price.
- Please create a celery task to fetches the ethereum price every 5 min and save the price into a Django model(more info in next section).
- Create schedule for tasks to run on recurring basis. If not done explicitly in code please leave instructions for us on how to setup/schedule.
- Extra credit: implment retry and/or exponential back off strategies to handle edge cases.
- More extra credit: create logging for task.

## Models

- Create a model that stores all data returned by the latest eth price endpoint including: ethbtc and ethusd.
- Please make sure to save a native datetime as well to be used in the API section.
- Assume this data will be used in time series data analysis as well as individual get requests.
- Extra credit: Feel free to index for performance.

## API

Please create the following endpoint:

### /eth/time

1. **/eth/time?before=<timestamp>&after=<timestamp>**

- Take in optional parameters before and after parameters and returns all necessary results.
- Using either your own code or django-rest-framework to implement limit/offset pagination in case results are long.

2. **eth/time?time=<timestamp>**

- take in timestamp and return closest possible eth price result.
- Show both requested time and returned time of price in result.
  Extra
- For extra consideration please write any test you find appropriate to insure the project requirements above are safely met.
- Feel free to explain your thought process anywhere in code comments. We find it beneficial to not only see the how but to also understand the why!

## Submission

For submission please compress your project into a .zip file and submit via email to kennyg@mvhq.io. If needed feel free to upload to a cloud provider(ex. Dropbox, Google Drive).

## Docs

### Cookiecutter-Django

- [Github](https://github.com/cookiecutter/cookiecutter-django)
- [Docs](https://cookiecutter-django.readthedocs.io/en/latest/)

### Celery

- [Docs](https://docs.celeryq.dev/en/stable/django/first-steps-with-django.html)

### Django-Rest-Framework

- [Docs](https://www.django-rest-framework.org)

### Etherscan API

- [Docs](https://docs.etherscan.io)

## Getting Up and Running Locally With Docker

Please reference [Getting Up and Running Locally With Docker](https://cookiecutter-django.readthedocs.io/en/latest/developing-locally-docker.html) for setup/startup instructions.

## Settings

Moved to [settings](http://cookiecutter-django.readthedocs.io/en/latest/settings.html).

## Basic Commands

### Setting Up Your Users

- To create a **normal user account**, just go to Sign Up and fill out the form. Once you submit it, you'll see a "Verify Your E-mail Address" page. Go to your console to see a simulated email verification message. Copy the link into your browser. Now the user's email should be verified and ready to go.

- To create a **superuser account**, use this command:

      $ python manage.py createsuperuser

For convenience, you can keep your normal user logged in on Chrome and your superuser logged in on Firefox (or similar), so that you can see how the site behaves for both kinds of users.

### Type checks

Running type checks with mypy:

    $ mypy metaversehq_backend_assessment

### Test coverage

To run the tests, check your test coverage, and generate an HTML coverage report:

    $ coverage run -m pytest
    $ coverage html
    $ open htmlcov/index.html

#### Running tests with pytest

    $ pytest

### Live reloading and Sass CSS compilation

Moved to [Live reloading and SASS compilation](https://cookiecutter-django.readthedocs.io/en/latest/developing-locally.html#sass-compilation-live-reloading).

### Celery

This app comes with Celery.

To run a celery worker:

```bash
cd metaversehq_backend_assessment
celery -A config.celery_app worker -l info
```

Please note: For Celery's import magic to work, it is important _where_ the celery commands are run. If you are in the same folder with _manage.py_, you should be right.

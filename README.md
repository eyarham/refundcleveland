# Refund Cleveland

a website for residents to City of Cleveland change their Budget to show what they want the city to value and 
share their proposed budget with their elected councilperson in city government.

Project outline is at:
https://docs.google.com/document/d/1ydc5Bw0Ctp8LJFEWECu9f9wMeUfM-FKlhTROik0QJiY/edit

We have a [Miro Board](https://miro.com/app/board/o9J_kj4DePU=/) to sketch out a wireframe.

You can view our project, live, at https://refundcleveland.com

### Errors / Bugs:

If something is not behaving as you expected, it could be a bug, or if you have an idea, it can be reported in our issue tracker at https://github.com/opencleveland/refundcleveland

## How to become involved:

Join our slack channel - #refundcleveland. Complete self-sign up link https://opencle-slack.herokuapp.com/ to join our slack instance.

Most of our features, issues, and discussion is coordinated through our slack channel.

## Developer Instructions

### Configuring and running locally

Pre-Requisites:
- Git
- Python 3.9+
- PostgreSQL
- Mailgun API Key (if you wish to send out emails while testing)

#### Clone repo, create virtual environment, and install requirements

```sh
git clone https://github.com/eyarham/refundcleveland.git
cd refundcleveland
python -m venv .venv
source .venv/Scripts/activate
pip3 install -r requirements.txt
```

#### Start a PostgreSQL Container with Docker Compose

1. Install [Docker Desktop](https://www.docker.com/products/docker-desktop/)
1. Open Docker Desktop
1. From the repository directory, run `docker compose up -d`
1. Run the command `python3 manage.py migrate` within the command line to create tables within your database.

#### Add local settings

Copy and rename **local_settings_template.py** to **local_settings.py**, and fill in environmental variables:

`SECRET_KEY` -- Django’s Secret Key used by the project
`GOOGLE_API_KEY` -- Used for Google's Civic Information API to map Address to Political Ward
`MAILGUN_API_KEY` -- Used for the Mailgun API that sends out emails when a user submits a budget

`DATABASES` -- map of parameters to define the connection to a database.  In prod, we are using a postgres db hosted on heroku, and the connection is injected there via config vars.  For local versions, enter the information you used when creating the database.  Example:
```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': 'refund1',
        'USER': 'postgres',
        'PASSWORD': '<password>',
        'HOST': 'localhost',
        'PORT': '5432',
    }
}
```

#### Run the app

```sh
python3 manage.py runserver
```

Navigate to http://localhost:8000/

### Running in a production environment
This is currently done through heroku.

### Dependencies
We used the following open source libraries/tools:
d3, django, python3, postgres, Google Civic Information API

### Note on Patches/Pull Requests 

* Fork the project.
* Make your feature addition or bug fix.
* Send us a pull request. Bonus points for making a new name your branch that describes your changes. For example, if you're improving the css by adding margins for input range element, `css-range-margins` would be appropriate. 

### Copyright

MIT License

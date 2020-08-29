# Django Boilerplate Project v1.1
A boilerplate project for Django to fast initialization.

All backend code follows [PEP8 style guidelines](https://www.python.org/dev/peps/pep-0008/).

Useful Links
- [pycodestyle Error Codes](https://pycodestyle.pycqa.org/en/latest/intro.html#error-codes)
- [flake8 Error Codes](https://flake8.pycqa.org/en/3.1.1/user/error-codes.html)

## Getting Started
### Steps
1. Clone/pull/download this repository
2. Install Miniconda
3. Create virtual environment and install dependencies
3. Configure the env variables. Use src/.env for development. For porduction, set them in the OS.
4. Rename the project.
```bash
#Syntax
python manage.py rename <current_project_name> <new_project_name>

#Example
python manage.py rename demo my_project
```
5. Generate Secret Key
Use this key as your SECRET_KEY.
Replace SECRET_KEY in 'src/.env'.

	- Method 1
```bash
python manage.py shell
```
```python
from django.core.management.utils import get_random_secret_key

print(get_random_secret_key())
```

	- Method 2
```bash
python -c "from django.core.management.utils import get_random_secret_key; print(get_random_secret_key())"
```

#### Installing MiniConda
Download and install MiniConda from [here](https://docs.conda.io/en/latest/miniconda.html).
> It is used to create and manage the virtual environment.
> pip freeze > requirements.txt is used to create the dependency list.

#### Create Virtual Environment and Install Dependencies
```bash
conda create --name env_dj python=3.7
conda activate env_dj
pip install -r requirements.txt
```

#### Key Dependencies
- django - A Python based web framework.
- pillow - A library to manage images in Django Apps.
- flake8 - Used for mainting the linting with VSCode.
- autopep8 - Used for few auto linting with VSCode.
- django-debug-toolbar - To manage debugging in development mode.

##### Installation
`pip install django, pillow, flake8, autopep8, django-debug-toolbar`
> Included in requirements.txt - external installation not required.

#### Opional Dependencies
- django-crispy-forms - A Library to integrate Django forms with Bootstrap.
- django-allauth - Used for authentication.
- django-countries - Used to list countries.

##### Installation
`pip install django-crispy-forms, django-allauth, django-countries`
> Included in requirements.txt - external installation not required.

## Database Setup
### Development
SQLite database is used for development. It is configured automatically by Django.

### Production
With Postgres, create a database named **testdb**
`createdb testdb`
> Make sure to include the database credentials in **env_file.py**

## Running the server
From the project directory to run the server, execute:
```bash
conda activate env_dj
python manage.py runserver
```

## Important Note
- Uncomment '.env' inside .gitignore so that .env file is not uploaded in the repository.
- Edit '.vscode/settings.json' ss per your choices.
- You must generate a new secret key for your project.

## Production Note
- Make sure to set environmental variable DEBUG=False.

## Author
Himel Das

## Acknowledgement
This boilerplate is an extension of the boilerplate by justdjango. I studied the YouTube videos on this topic by JustDjango YouTube channel while creating this boilerplate.
Thanks to justdjango for creating such an amazing boilerplate and step by step tutorial.

* [Django Project Boilerplate by justdjango](https://github.com/justdjango/django_project_boilerplate)
* [How to Create a Boilerplate for Django Project](https://www.youtube.com/watch?v=GEogao-tUec)

## Note
For special commands and detailed note refer to the following links:
- [COMMANDS.md](COMMANDS.md)
- [NOTE.md](NOTE.md)

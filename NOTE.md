# Note on Django Boilerplate Project

## Lesson 1 - Setting up the Debug Toolbar
### Section 1.1 - Project Initialization
- Install miniconda from [here](https://docs.conda.io/en/latest/miniconda.html)
- Create and activate a virtual environment.
```bash
prompt $g
conda remove --name env_dj --all
conda create --name env_dj python=3.7
conda activate env_dj
pip install -r requirements.txt
pip freeze > requirements.txt
```

- Install Django. `pip install django`
- Start a project named 'demo'. `django-admin startproject demo`
- It will create a directory 'demo' having all the related files.
- Rename this 'demo' to 'src'.

### Section 1.2 - Installing Django Debug Toolbar
Django Debug Toolbar is used to have a look at the underlying information.
[Installation](https://django-debug-toolbar.readthedocs.io/en/latest/installation.html)

- Install DDT. `pip install django-debug-toolbar`
- Include 'debug_toolbar' in the INSTALLED_APPS of src/demo/settings.py
- Include the following lines in the settings.py.
```bash
STATIC_URL = '/static/'
STATICFILES_DIRS = [os.path.join(BASE_DIR, 'static_files')]
STATIC_ROOT = os.path.join(BASE_DIR, 'static')

# Media files (Uploaded by the users)
MEDIA_URL = '/media/'
MEDIA_ROOT = os.path.join(BASE_DIR, 'media')
```

- Create directory src/static_files
- Add this on the bottom of demo/urls.py
```python
from django.conf import settings
from django.urls import include, path


if settings.DEBUG:
    import debug_toolbar
    # For Django Debug Toolbar in debug mode.
    urlpatterns += [path('__debug__/', include(debug_toolbar.urls))]

    # To serve static files in debug mode
    urlpatterns += static(settings.STATIC_URL,
                          document_root=settings.STATIC_ROOT)
    # To serve media files in debug mode
    urlpatterns += static(settings.MEDIA_URL,
                          document_root=settings.MEDIA_ROOT)
```

- Add DDT MIDDLEWARE in settings.py
- Add INTERNAL_IPS to settings.py
```python
INTERNAL_IPS = ['127.0.0.1',]
```

- Add DEBUG_TOOLBAR_PANELS to settings.py from [here](https://django-debug-toolbar.readthedocs.io/en/latest/configuration.html)
- Add DEBUG_TOOLBAR_CONFIG in settings.py
- [Optional] You can run collectstatic command to fetch all the django backend static files. In will create src/static_root directory with other directories like admin, debug_toolbar, etc.
[More Info](https://docs.djangoproject.com/en/3.1/ref/contrib/staticfiles/).
`python manage.py collectstatic`

### Section 1.3 - Configure templates
- On the top of settings.py under BASE_DIR, add TEMPLATE_DIR.
```python
TEMPLATE_DIR = os.path.join(BASE_DIR, 'templates')
```

- Edit DIRS of TEMPLATES in settings.py
```python
TEMPLATES = [
    {
        ...
        'DIRS': [TEMPLATE_DIR],
        ...
    },
]
```
- Create directory src/templates
- Create src/templates/base.html and src/templates/home.html

## Lesson 2 - Setting up Multiple Settings Modules
### Section 2.1 -

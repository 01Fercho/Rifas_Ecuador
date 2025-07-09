git init
git remote add origin https://github.com/01Fuertes/rifas_ecuador.git
git add .
git commit -m "Proyecto inicial de sitio de rifas"
git branch -M main
git push -u origin main

importar sistema operativo
importar dj_database_url
desde pathlib importar Path

# DIRECTORIO BASE
BASE_DIR = Ruta(__archivo__).resolve().padre.padre

# CLAVE SECRETA
SECRET_KEY = os.environ.get('DJANGO_SECRET_KEY', 'clave-secreta-por-defecto')

# DEPURACIÓN
DEBUG = os.environ.get('DEBUG', 'Falso') == 'Verdadero'

# ANFITRIONES PERMITIDOS
HOSTS_PERMITIDOS = os.environ.get('HOSTS_PERMITIDOS', 'localhost').split(',')

# Aplicaciones necesarias
APLICACIONES_INSTALADAS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.tiposdecontenido',
    'django.contrib.sessions',
    'django.contrib.mensajes',
    'django.contrib.archivos estáticos',
    #tus aplicaciones aquí
]

# Middleware
MIDDLEWARE = ​​[
    'django.middleware.security.SecurityMiddleware',
    'ruido blanco.middleware.WhiteNoiseMiddleware',
    'django.contrib.sessions.middleware.SessionMiddleware',
    'django.middleware.common.CommonMiddleware',
    'django.middleware.csrf.CsrfViewMiddleware',
    'django.contrib.auth.middleware.AuthenticationMiddleware',
    'django.contrib.messages.middleware.MessageMiddleware',
    'django.middleware.clickjacking.XFrameOptionsMiddleware',
]

ROOT_URLCONF = 'rifas_ecuador.urls'

PLANTILLAS = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [BASE_DIR/'plantillas'],
        'APP_DIRS': Verdadero,
        'OPCIONES': {
            'procesadores_de_contexto': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]

WSGI_APPLICATION = 'rifas_ecuador.wsgi.application'

# Base de datos
BASES DE DATOS = {
    'predeterminado': dj_database_url.config(
        predeterminado=os.environ.get('URL_DE_LA_BASE_DE_DATOS'),
        edad máxima de conexión=600,
        ssl_require=Verdadero
    )
}

# Validación de contraseña
VALIDADORES DE CONTRASEÑA DE AUTORIZACIÓN = [
    {
        'NOMBRE': 'django.contrib.auth.password_validation.UserAttributeSimilarityValidator',
    },
    {
        'NOMBRE': 'django.contrib.auth.password_validation.MinimumLengthValidator',
    },
]

#Internacionalización
CÓDIGO_DE_IDIOMA = 'es'
ZONA HORARIA = 'América/Guayaquil'
USE_I18N = Verdadero
USE_TZ = Verdadero

# Archivos estáticos
STATIC_URL = '/estático/'
RAÍZ_ESTÁTICA = DIR_BASE / 'archivos estáticos'

STATICFILES_STORAGE = 'whitenoise.storage.CompressedManifestStaticFilesStorage'

# HTTPS y Render
ENCABEZADO_SSL_PROXY_SEGURO = ('PROTO_HTTP_X_REENVIADO', 'https')

# Correo electrónico
EMAIL_BACKEND = 'django.core.mail.backends.smtp.EmailBackend'
EMAIL_HOST = 'smtp.gmail.com'
PUERTO DE CORREO ELECTRÓNICO = 587
EMAIL_USE_TLS = Verdadero
USUARIO_DEL_HOST_DE_CORREO_ELECTRÓNICO = os.environ.get('USUARIO_DEL_HOST_DE_CORREO_ELECTRÓNICO')
CONTRASEÑA_DEL_HOST_DE_EMAIL = os.environ.get('CONTRASEÑA_DEL_HOST_DE_EMAIL')
git clone https://github.com/01Fercho/rifas_ecuador.git
cd rifas_ecuador
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python manage.py runserver
python manage.py shell
from core.views import run_draw
run_draw(<raffle_id>)
dj-database-url
psycopg2-binary
whitenoise
import os
import dj_database_url
from pathlib import Path

BASE_DIR = Path(__file__).resolve().parent.parent

SECRET_KEY = os.getenv('DJANGO_SECRET_KEY', 'change-me')
DEBUG = os.getenv('DEBUG', 'False') == 'True'

ALLOWED_HOSTS = os.getenv('ALLOWED_HOSTS', '').split(',')

# Database
DATABASES = {
    'default': dj_database_url.config(
        default=os.getenv('DATABASE_URL'),
        conn_max_age=600,
        ssl_require=True
    )
}

# Static files
MIDDLEWARE = [
    'django.middleware.security.SecurityMiddleware',
    'whitenoise.middleware.WhiteNoiseMiddleware',
    # ...
]
STATIC_ROOT = BASE_DIR / 'staticfiles'
STATICFILES_STORAGE = 'whitenoise.storage.CompressedManifestStaticFilesStorage'

# Proxy SSL header
SECURE_PROXY_SSL_HEADER = ('HTTP_X_FORWARDED_PROTO', 'https')
#!/usr/bin/env bash
set -o errexit

pip install -r requirements.txt
python manage.py collectstatic --no-input
python manage.py migrate
web: gunicorn rifas_ecuador.wsgi:application
DATABASE_URL=<la URL de tu base de datos Render>
DJANGO_SECRET_KEY=...
DEBUG=False
ALLOWED_HOSTS=<tuServicio>.onrender.com
EMAIL_HOST_USER=...
EMAIL_HOST_PASSWORD=...
STRIPE_SECRET_KEY=...
STRIPE_WEBHOOK_SECRET=...
PAYPAL_CLIENT_ID=...
PAYPAL_SECRET=...

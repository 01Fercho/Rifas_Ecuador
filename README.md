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

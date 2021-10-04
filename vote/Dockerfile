#Empleo de imagen oficial de python
FROM python:3.9-slim

#Adición de curl y apache2-utils
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
    apache2-utils \
    curl \
    && rm -rf /var/lib/apt/lists/*

#Metadatos de la aplicación
LABEL maintainer="alejo.bernal22@gmail.com" \
    description="Aplicación frontend | Grupo 9 Módulo Contenedores" \
    version="1.0"

#Configuración de variables
ENV OPTION_A="perros"
ENV OPTION_B="gatos"

#Directorio de aplicación
WORKDIR /app

#Instalación de requermientos
COPY requirements.txt /app/requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

#Copiado de código
COPY . .

#Eposición de puerto
EXPOSE 80

#Ejecución de comandos al momento de ejecución
CMD ["gunicorn", "app:app", "-b", "0.0.0.0:80", "--log-file", "-", "--access-logfile", "-", "--workers", "4", "--keep-alive", "0"]

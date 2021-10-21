# Aplicación con Turbo Flask

## Descripción
Esta es una aplicación de muestra para probar la extensión Turbo Flask ¡, la cual permite actualización asincronica. Permite actualizar parte de la pagína web sin necesidad de refrescar.

Se puede obtener más información de Turbo Flask en el siguiente link: https://github.com/miguelgrinberg/turbo-flask

Veo importante destacar que el proyecto Turbo Flask es propiedad de Miguel Grinberg https://github.com/miguelgrinberg utilizando la biblioteca Turbo.js https://github.com/hotwired/turbo

Para este ejemplo utilizo como guía el tutorial practico esctrito por Miguel en su blog https://blog.miguelgrinberg.com/post/dynamically-update-your-flask-web-pages-using-turbo-flask

## Instalación

En su ambiente virtual instalar Flask 2 y Turbo Flask

```
(venv) $ pip3 install flask turbo-flask
```

## Explicación

Siguiendo el tutorial de Miguel, vamos a crear una web que nos brinde las cargas del CPU en los últimos 1,5 y 15 minutos, esto funciona para servidores Linux, en el mismo código de app.py también podemos encontrar un fracmeto que nos brinde datos aleatorios si el sistema operativo no es Linux:

```
@app.context_prrocessor
def inject_load():
    if sys.platform.startswith('linux'):
        with open('/proc/loadavg', 'rt') as f:
            load = f.read().split()[0:3]
    else:
        load = [int(random.random() * 100) / 100 for _ in range(3)]
    return{'load1': load[0], 'load5': load5[1], 'load15': load[2]}
    
´´´


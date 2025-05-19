# Práctica Final - Simulación de Red Hospitalaria

## Índice

1. [Introducción](#introducción)
2. [Objetivos](#objetivos)
3. [Tecnologías Utilizadas](#tecnologías-utilizadas)
4. [Diseño de la Red](#diseño-de-la-red)
5. [Configuración en GNS3](#configuración-en-gns3)
6. [Desarrollo de la Aplicación Web](#desarrollo-de-la-aplicación-web)
7. [Monitorización y Gestión de Routers](#monitorización-y-gestión-de-routers)
8. [Código Fuente Relevante](#código-fuente-relevante)
9. [Pruebas Realizadas](#pruebas-realizadas)
10. [Resultados y Capturas](#resultados-y-capturas)
11. [Conclusiones](#conclusiones)
12. [Posibles Mejoras](#posibles-mejoras)

---

## Introducción

Este proyecto consiste en la simulación de la infraestructura de red de dos hospitales independientes utilizando GNS3. Cada hospital cuenta con su propia red local y está gestionado por dos routers: un router principal (master) y un router de respaldo (backup), lo que permite asegurar la continuidad del servicio en caso de fallos.

Como complemento, se ha desarrollado una aplicación web con Python, desde la cual es posible gestionar y monitorizar el estado de todos los routers en ambas redes. Esta herramienta permite detectar en tiempo real si un router está activo o caído, y ofrece una interfaz centralizada para la supervisión del estado de la infraestructura de red de cada hospital.

## Objetivos

- Diseñar una red hospitalaria realista en GNS3.
- Desarrollar una aplicación web para mostrar el estado de los routers.
- Poder acceder a los routers desde la aplicación web.

## Tecnologías Utilizadas

- GNS3
- Python con falsk
- HTML/JavaScript
- SNMP
- GitHub para la documentación

## Diseño de la Red

![image](https://github.com/user-attachments/assets/c414bddf-c0a9-4e68-9ddf-15173d80badf)

Describe:
- Hay cuatro routers (dos para cada hospital), dos switches (uno cada hospital) y dos equipos para sumilar los equipos de un hospital (uno para cada hospital).
- La imagén se basa en dos hospitales: hospital de Badajóz y hospital de Mérida.

## Configuración en GNS3

- Hay un archivo llamado configuración de los routers donde aparece los running config de los routers.

## Desarrollo de la Aplicación Web

- Wocu es una aplicación web desarrollada en Python que permite gestionar y monitorizar routers de manera centralizada a través de una interfaz intuitiva. Su objetivo principal es facilitar la supervisión del estado de la infraestructura de red de cada hospital simulado en el proyecto.
- La manera en la que Wocu se comunica con los routers es mediante SNMP (Simple Network Management Protocol), un protocolo estándar ampliamente utilizado para la monitorización y gestión de dispositivos de red. Wocu actúa como un cliente SNMP, enviando solicitudes a los routers y procesando las respuestas para mostrarlas de forma clara y visual al usuario.

![image](https://github.com/user-attachments/assets/72babb21-1821-4d04-a8b3-8bdcff004b3c)


## Monitorización y Gestión de Routers

- Para detectar si un router está caído o activo se utiliza el protocolo SNMP (Simple Network Management Protocol). La aplicación realiza consultas SNMP a cada router, si el dispositivo responde correctamente, se considera que está encendido y operativo. En cambio, si no se recibe respuesta, se interpreta que el router está apagado o inaccesible.
- La aplicación permite personalizar la información SNMP que se desea visualizar de cada router, adaptándose a las necesidades del usuario o al entorno de red, si clickas [aquí](https://mibbrowser.online/mibdb_search.php) podrás ver algunos OID's para usar.


## Código Fuente Relevante

Incluye aquí fragmentos de:
- Código Python para conexión/monitorización.

```python
hola
```
- Scripts importantes.

```JavaScrpt
hola
```
# Código para conectarse a un router y verificar estado


## Código Fuente Relevante


## Pruebas Realizadas


## Resultados y Capturas


## Conclusiones


## Posibles Mejoras


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
9. [Manual Técnico](#manual-técnico)
10. [Manual Usuario](#manual-usuario)
11. [Pruebas Realizadas](#pruebas-realizadas)
12. [Resultados y Capturas](#resultados-y-capturas)
13. [Conclusiones](#conclusiones)
14. [Posibles Mejoras](#posibles-mejoras)

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

- Algunas configuraciones importantes han sido:
  - **VRRP**: Para que cuando el router MASTER caiga se levante el de BACKUP
  - **sadasda**
  - **asdasd**

- Hay un archivo llamado configuración de los routers donde aparece los running config de los routers.

## Desarrollo de la Aplicación Web

- Wocu es una aplicación web desarrollada en Python que permite gestionar y monitorizar routers de manera centralizada a través de una interfaz intuitiva. Su objetivo principal es facilitar la supervisión del estado de la infraestructura de red de cada hospital simulado en el proyecto.
- La manera en la que Wocu se comunica con los routers es mediante SNMP (Simple Network Management Protocol), un protocolo estándar ampliamente utilizado para la monitorización y gestión de dispositivos de red. Wocu actúa como un cliente SNMP, enviando solicitudes a los routers y procesando las respuestas para mostrarlas de forma clara y visual al usuario.

![image](https://github.com/user-attachments/assets/72babb21-1821-4d04-a8b3-8bdcff004b3c)


## Monitorización y Gestión de Routers

- Para detectar si un router está caído o activo se utiliza el protocolo SNMP (Simple Network Management Protocol). La aplicación realiza consultas SNMP a cada router, si el dispositivo responde correctamente, se considera que está encendido y operativo. En cambio, si no se recibe respuesta, se interpreta que el router está apagado o inaccesible.
- La aplicación permite personalizar la información SNMP que se desea visualizar de cada router, adaptándose a las necesidades del usuario o al entorno de red, si clickas [aquí](https://mibbrowser.online/mibdb_search.php) podrás ver algunos OID's para usar.

# Manual Técnico

Aquí explicaremos paso a paso los detalles y como se ha ido creando la estructura de red, la aplicación y sus funcionamientos.

Esta es la estructura de la red.

![image](https://github.com/user-attachments/assets/c414bddf-c0a9-4e68-9ddf-15173d80badf)

Hemos usado la aplicación GNS3, en esta aplicación hay que importar las IOS de los equipos para poder crear la estructura de red. Te descargas la IOS de los routers por [aquí](https://lomboknetworking.blogspot.com/p/cisco-ios-gns3.html).

Y para importar la IOS a GNS3 hay que meterse en Edit->Preferences-> IOS Routers. Le das en New y seleccionas la IOS descargada y vas configurando el router a tu gusto con el nombre de este, los puertos que quieres que tenga, la velocidad de RAM...

![image](https://github.com/user-attachments/assets/4da44ae4-49f3-446c-b176-d2e142624a00)

La configuración de la nube para que los routers tengan salida a internet es la siguiente. Primero de todo se ha creaado una red puente que es una interfaz de red virtual, esto se hace porque linux no permite que se conecte directamente a tu host (eth0).

Se crea el puente.

![image](https://github.com/user-attachments/assets/ec3d197a-7013-4f67-bd4d-1892b788aeda)

Se levanta la interfaz.

![image](https://github.com/user-attachments/assets/0da937ee-1bea-4564-aa5b-1fd128d392fd)

Se la asigna una IP al puente.

![image](https://github.com/user-attachments/assets/618dbd12-2e21-4960-babc-cfad2a9f67ef)

Y verificamos que todo haya salido bien.

![image](https://github.com/user-attachments/assets/1f363308-db6d-42a2-b17f-e0668d1b29cd)

Ahora hay que vincular las IPs que van a utilizar los routers al puente creado. Primero a crearlas.

Creamos la la interfaz tipo TAP.

![image](https://github.com/user-attachments/assets/c391afdd-a48a-4247-b95c-89283b13fea0)

Levantamos la interfaz.

![image](https://github.com/user-attachments/assets/2a52a3bd-f866-4dfd-a55a-546ad4ce96b8)

Asignamos una IP a TAP.

![image](https://github.com/user-attachments/assets/d91ed114-3c05-4847-904c-05881003b166)

Y ahora si vinculamos la interfaz TAP a la interfaz puente.

![image](https://github.com/user-attachments/assets/f332db78-7b63-4e7f-9e60-2a69e03e0a01)

Esto lo haríamos con todas las IPs que necesitaramos, en mi caso 4. Para comprobar que se ha hecho todo bien con ```ip addr show```

![image](https://github.com/user-attachments/assets/c32bcd96-dcc7-4ee2-83cf-999be61179a9)


Este pasoe es importante, porque es para hacer que estos cambios perduren aunque se reinicie el equipo.

Nos movemos a ```/etc/systemd/network/``` y creamos 2 ficheros:

```br0.netdev```

![image](https://github.com/user-attachments/assets/a9a8dff6-9629-4fa2-8740-8d4434d2441c)

```br0.network```

![image](https://github.com/user-attachments/assets/e72c5fb8-52ee-4bf2-94ca-9a878979e8c5)

Y ahora lo mismo con los TAP.

```tap0.netdev```

![image](https://github.com/user-attachments/assets/5a10d0de-a44e-4ec0-b51f-c1ae7f8be65a)

```tap0.network```

![image](https://github.com/user-attachments/assets/0d4cd88c-641b-4703-a563-0ab660758750)

Y así lo repetiríamos con todos los TAP que tuvueramos.


Ahora que ya tenemos IPs disponibles para los routers tocaría configurarlos.

Le asignamos la IP 10.0.0.2 que es la del tap0 al puerto g0/0 y se define que es la red externa (WAN).

![image](https://github.com/user-attachments/assets/eb7e6a69-4d52-45b2-b4cb-5962e11ca214)

Le asignamos la IP 192.168.10.1 al puerto g1/0 y se define que es la red interna (LAN). También configuramos el vrrp para que cuando se caiga el master se levante el backup.

![image](https://github.com/user-attachments/assets/e647b5ba-7f77-4339-adcc-e9fa13a2400d)

Creamos una access-list que permita el tráfico de cualquier IP que venga de 192.168.10.x y lo hace NAT overload para que sepa la salida a internet.

![image](https://github.com/user-attachments/assets/f2ff6f13-bb3d-4a6b-952b-813566314d20)
![image](https://github.com/user-attachments/assets/ea2add78-bccd-4148-9e42-a18d01d095c1)

Creamos una ip route para que sepa donde enviar el tráfico externo.

![image](https://github.com/user-attachments/assets/ab67a83d-a6e5-45aa-b8d2-4be2b97ab659)

Habilitar SNMP para que mande las peticiones a la aplicación.

![image](https://github.com/user-attachments/assets/12885c4d-c32d-49e7-a450-741112d948c3)

Configuraciones necesarias para poder tener un mínimo de seguridad y para poder conectarse con ssh.

![image](https://github.com/user-attachments/assets/9aed57e2-72eb-4ef0-9c69-6893cded5113)

Esta configuración la repetiriamos en todos los routers cambiando 2 cosas, las IPs de estos y dependiendo de si son el router MASTER o el de BACKUP que cambiariamos el orden de prioridad de estos.

Ahora viene la configuración de la aplicación para recoger todas las peticiones que manda SNMP y traducirlas a algo que sea facil de interpretar en nuestra aplicación web.

```python
from flask import Flask, jsonify, send_from_directory, request
from pysnmp.hlapi import SnmpEngine, CommunityData, UdpTransportTarget, ContextData, ObjectType, ObjectIdentity, getCmd
from flask_cors import CORS
```
Se importan librerías:

```Flask```: el framework web (sirve para crear el servidor web).

```jsonify```: convierte datos de Python en JSON para enviar al navegador.

```send_from_directory```: sirve para enviar archivos HTML u otros del servidor al navegador.

```request```: permite leer datos que llegan al servidor (por ejemplo, de formularios).

```pysnmp.hlapi```: se usa para enviar comandos SNMP (una forma de obtener info de routers/switches).

```CORS```: permite que otras páginas web accedan a esta API (muy útil si tienes frontend separado del backend).

```python
app = Flask(__name__, static_folder='public')
CORS(app)
```

```app = Flask(__name__)```: crea la app Flask. Es el "servidor web".

```static_folder='public'```: le dice a Flask que los archivos HTML, CSS, JS están en la carpeta public.

```CORS(app)```: permite que cualquier frontend se conecte sin restricciones de origen.

```python
DEVICES = [
    {
        "name": "MERIDA-MASTER",
        "ip": "10.0.0.2",
        "community": "COMUNIDAD_RO",
        "oids": {
            "uptime": "1.3.6.1.2.1.1.3.0",
            "interfaces": {
                "name": "1.3.6.1.2.1.2.2.1.2",
                "status": "1.3.6.1.2.1.2.2.1.8",
                "rx": "1.3.6.1.2.1.2.2.1.10",
                "tx": "1.3.6.1.2.1.2.2.1.16"
            }
        }
    }
...
```
Dentro de DEVICES es donde guardaremos los routers que vamos a monitorear por SNMP y los datos que queremos mostrar de cada uno.

```python
if __name__ == "__main__":
    app.run(debug=True, host="0.0.0.0", port=5000)
```
Este comando hace que el servidor Flask se ejecute en el puerto 5000 y escuche todas las IPs

Ahora explicaré las partes importantes de mi código de JavaScrpt.

```JavaScrpt
const response = await fetch("/api/devices");
const devices = await response.json();
```
Con este codígo se conecta a la aplicacíon de python y le pide los datos de los routers definidos.

```JavaScrpt
.forEach(device => {
            let estado = "Encendido";
            let statusClass = "has-text-success";

            for (const key in device.data) {
              const val = device.data[key];
              if (
                val.toLowerCase().includes("timeout") ||
                val.toLowerCase().includes("no such") ||
                val.toLowerCase().includes("error")
              ) {
                estado = "Apagado";
                statusClass = "has-text-danger";
                break;
              }
            }
```

Si el router da señales, en la página aparecerá como "Encendido", pero si da algún error, tarda demasido o no se encuentra, aparecerá como "Apagado".

```JavaScrpt
const history = data.data.history || [];
```
El código JavaScript hace una consulta al backend en Python, que responde con datos en JSON. La información del historial proviene de una variable global llamada HISTORY, donde se guarda el estado de conectividad del router.

# Manual Usuario

Para encender la aplicación nos tendremos que ir a nuestra carpeta de trabajo y ejecutar app.py.

Activamos el entorno virtual para poder usar Python y ejecutamos la aplicación, veremos que empezarán a llegar las peticiones que hace la aplicación.

![image](https://github.com/user-attachments/assets/85f573d2-4aa1-46cd-a5a1-a047efff6a6c)

Una vez la aplicacíon está en marcha, nos dirijiremos a nuestro navegador y nos entraremos a la siguiente direccion [http://localhost:5000/](http://localhost:5000/) que es el puerto donde se está ejecutando la aplicación.

Tendremos que poner nuestras credenciales para acceder.

![image](https://github.com/user-attachments/assets/0257723e-8b17-4e03-ad59-6681924b97b4)

Una vez acedemos, nos aparecerán los routers que estamos monitorizando y algo de información de cada uno. Si seleccionamos alguno de ellos, nos llevará a otra página donde nos dará más información.

![image](https://github.com/user-attachments/assets/4445c8c5-ded7-4603-8e33-ee6c1710135c)

Aquí podremos ver una gráfica de la conectividad del router y las interfaces que tiene levantadas o bajadas.

![image](https://github.com/user-attachments/assets/031e9af7-8949-49fa-b240-0dbd408d6113)

Si necesitamos hacer pruebas a los routers, nos podremos conectar a ellos con ssh. Abrimos la terminal y ejecutamos lo siguiente, el usuario que en este caso será siempre admin y la IP del router que queramos acceder.

![image](https://github.com/user-attachments/assets/e594ebcd-ed3d-456e-93e2-c96b42441fd5)

## Conclusiones


## Posibles Mejoras


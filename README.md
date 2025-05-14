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

Breve descripción del proyecto: simular una red hospitalaria con routers, switches y dispositivos, gestionar el estado de la red mediante una aplicación web y automatizar la monitorización usando Python.

## Objetivos

- Diseñar una red hospitalaria realista en GNS3.
- Automatizar la supervisión de dispositivos de red.
- Desarrollar una aplicación web para mostrar el estado de la red.
- Utilizar herramientas modernas de programación (Python, Flask/Django, etc.).

## Tecnologías Utilizadas

- GNS3
- Python (con librerías como Netmiko, Paramiko, Flask)
- HTML/CSS/JavaScript
- Bootstrap/Tailwind (si usaste algún framework)
- SNMP o ping (para monitoreo)
- GitHub para versionado y documentación

## Diseño de la Red

Describe:
- Cuántos routers, switches y PCs usaste.
- Qué representa cada parte (área quirúrgica, laboratorio, administración...).
- Añade un diagrama (puede ser una imagen exportada de GNS3).

## Configuración en GNS3

- Descripción de cómo configuraste los routers.
- Configuración de IPs, protocolos de enrutamiento (OSPF, RIP...).
- Scripts o comandos usados.

## Desarrollo de la Aplicación Web

- Qué hace tu aplicación.
- Framework usado (Flask, Django...).
- Cómo se comunica con los routers (via SSH, SNMP...).
- Capturas de pantalla si es posible.

## Monitorización y Gestión de Routers

- Cómo detectas si un router está caído o no (ping, SNMP, SSH).
- Cómo se refleja esa información en tu página.
- Automatización: ¿cada cuánto se actualiza?, ¿usas hilos o cron jobs?

## Código Fuente Relevante

Incluye aquí fragmentos de:
- Código Python para conexión/monitorización.
- Código HTML de la página principal.
- Scripts usados para automatizar.

Puedes usar bloques de código:

```python
import netmiko
```
# Código para conectarse a un router y verificar estado

## Código Fuente Relevante

## Pruebas Realizadas

-Qué pruebas hiciste para asegurar el funcionamiento (apagar routers, cortar interfaces...).
-Resultados esperados y observados.

## Resultados y Capturas

-Muestra ejemplos visuales del sistema funcionando.
-Estado de routers, logs generados, interfaz web...

## Conclusiones

-Qué aprendiste.
-Qué desafíos encontraste y cómo los resolviste.

## Posibles Mejoras

-Integrar una base de datos.
-Dashboard más visual.
-Alertas por correo o Telegram.
-Escalabilidad para más nodos.

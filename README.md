# ASIX2_Monitorización y Gestión de Dispositivos de Red_TMD <br> Desarrolladores: Miquel Burguera, Tim Kalugin, David Valverde.

## 💡  Explicación de la idea del proyecto
<details>
  <summary>Explicación 🔽</summary>
Monitorización y Gestión de Dispositivos de Red

Este proyecto desarrolla una **aplicación web** destinada al **análisis de redes** y la **gestión de dispositivos** en infraestructuras empresariales. La plataforma ofrece un **dashboard interactivo** que permite monitorizar en tiempo real el **uso de CPU y memoria** de dispositivos de red como routers y switches, así como el **ancho de banda consumido** por los clientes y la identificación de **dispositivos conectados** mediante DHCP. Además, facilita la **configuración remota** de servidores DHCP y DNS, y la **gestión automatizada de reglas de firewall** a través de scripts personalizados.

Para la recopilación de datos, se emplean protocolos como **SNMP** o **Netconf**. El procesamiento y la interacción con los dispositivos se realizan utilizando **PHP** y **Python**, mientras que la visualización de métricas se implementa con **Grafana** o **Chart.js**. La interfaz web está servida por **Nginx**, y el almacenamiento de datos se gestiona mediante una base de datos **MySQL**.

Esta solución centraliza y optimiza la **monitorización** y **administración de redes**, mejorando la **eficiencia operativa** y reforzando la **seguridad** en entornos corporativos.

**Palabras clave**: análisis de red, gestión de dispositivos, monitorización, SNMP, Netconf, automatización de firewall, PHP, Python, Grafana, Chart.js, Nginx, MySQL.
</details>

<details>
<summary>Funcionalidades 🔽</summary>
  
  - Uso de CPU y memoria de dispositivos (routers, switches).
  - Ancho de banda usado por los clientes.
  - Dispositivos conectados a través de DHCP.
  - Configuración básica remota de servidores DHCP y DNS.
  - Gestión de reglas de firewall mediante scripts automatizados.
</details>

## 💻  Tecnologías a utilizar (lenguajes, framework, sistemas, software...)
<details>
  <summary>Front-end 🔽</summary>

  - HTML
  - CSS
  - Bootstrap
  - Colores a utilizar en el front-end: pendientes a elegir
</details>

<details>
  <summary>Back-end 🔽</summary>

   - Python 
   - PHP
</details>

<details>
  <summary>Base de Datos 🔽</summary>
  
  - MySql
</details>

<details>
  <summary>Framework 🔽</summary>
  
  - API de Python con flask
</details>

<details>
  <summary>Software 🔽</summary>
  
  - Visual Studio
  - Trello
  - GitHub
  - Cloudflare
  - Pi-hole
  - Nginx
  - Grafana
</details>

## :whale:  Docker
<details>
  <summary>Información básica 🔽</summary>

¿Qué son los contenedores de docker?
  - La función principal de los contenedores Docker es desarrollar, enviar y ejecutar cualquier aplicación en cualquier sistema, constituyéndose así como una alternativa flexible y capaz de ahorrar recursos frente a la emulación de componentes de hardware basada en máquinas virtuales (VM).

¿Qué diferencias hay entre los contenedores de docker y los lxc?
  - LXC: es un tipo de contenedor de sistema lo que significa que todos los contenedores creados con LXC necesitan un sistema operativo propio para funcionar, podemos tener en un solo contenedor diferentes aplicaciones, más parecido a una máquina virtual, es neutral en cuanto al sistema de archivos, permite guardar datos dentro o fuera del contenedor, facilita la construcción de pilas acopladas o compuestas.
  - Docker: utiliza el sistema operativo del sistema anfitrión, solo un contenedor para un servicio, es más ligero y modular, se basa en capas de solo lectura mediante AUFS o DeviceMapper, sus instancias son efímeras, y los datos persistentes deben almacenarse en bind mounts o volúmenes de datos.

¿Cuál es la diferencia entre una imagen y un contenedor en docker?
  - Imagen: una imagen es una plantilla fija que contiene el sistema de archivos y la configuración necesarios para ejecutar una aplicación. Si se necesita realizar cambios, hay que crear una nueva imagen

</details>






![image](https://github.com/user-attachments/assets/f267646b-97b2-499a-8770-e1064f8b3263)



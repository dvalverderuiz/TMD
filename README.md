# ASIX2_Monitorización y Gestión de Dispositivos de Red_TMD <br> Desarrolladores: Miquel Burguera, Tim Kalugin, David Valverde.

## 📄 ABSTRACT

### Castellano
Este proyecto integra redes, sistemas operativos, programación y ciberseguridad para construir una infraestructura empresarial simulada y escalable. Sobre Proxmox, hemos desplegado un entorno completo donde pfSense actúa como router, firewall, servidor DHCP y DNS, gestionando dos redes: una genérica con un servidor Docker que aloja una web estática, y una red empresarial simulada con servidores, servicios (Grafana, Prometheus, Suricata) y puestos de trabajo virtualizados. El núcleo del proyecto es una herramienta de linux desarrollada en Python y SNMP para el monitoreo y análisis de red, que “vendemos” como producto a empresas para mejorar su seguridad y control. A lo largo del proyecto hemos cumplido nuestras expectativas iniciales, logrando una base sólida y funcional; sin embargo, reconocemos que hay aspectos que no hemos podido completar por tiempo, aunque hemos diseñado el sistema pensando en que pueda escalarse fácilmente en el futuro con nuevas funcionalidades y servicios.

### Català
Aquest projecte integra xarxes, sistemes operatius, programació i ciberseguretat per construir una infraestructura empresarial simulada i escalable. Sobre Proxmox, hem desplegat un entorn complet on pfSense actua com a router, tallafoc, servidor DHCP i DNS, gestionant dues xarxes: una genèrica amb un servidor Docker que allotja una web estàtica, i una xarxa empresarial simulada amb servidors, serveis (Grafana, Prometheus, Suricata) i llocs de treball virtualitzats. El nucli del projecte és una aplicació web desenvolupada en Python i SNMP per al monitoratge i anàlisi de xarxa, que “venem” com a producte a empreses per millorar la seva seguretat i control. Al llarg del projecte hem complert les expectatives inicials, aconseguint una base sòlida i funcional; no obstant això, reconeixem que hi ha aspectes que no hem pogut completar per temps, encara que hem dissenyat el sistema pensant en què es pugui escalar fàcilment en el futur amb noves funcionalitats i serveis.

### English
This project integrates networking, operating systems, programming, and cybersecurity to build a simulated and scalable enterprise infrastructure. On Proxmox, we have deployed a complete environment where pfSense acts as a router, firewall, DHCP server, and DNS, managing two networks: a generic one with a Docker server hosting a static website, and a simulated company network with servers, services (Grafana, Prometheus, Suricata), and virtual workstations. The core of the project is a web application developed in Python and SNMP for network monitoring and analysis, which we present as a product for companies to improve their security and control. Throughout the project, we have met our initial expectations, achieving a solid and functional base; however, we acknowledge that some aspects were left incomplete due to time constraints, but we have designed the system with future scalability in mind, allowing for new features and services to be added later.

---

## 💡 EXPLICACIÓN DEL PROYECTO
<details>
<summary>Contexto del proyecto 🔽</summary>

  El proyecto nace en el marco de un módulo multidisciplinar donde se combinan conocimientos de redes, sistemas operativos, programación y ciberseguridad para diseñar y desplegar una infraestructura empresarial simulada. El objetivo era construir un entorno virtualizado que reflejara de forma realista cómo operan las redes corporativas modernas, incorporando servicios esenciales, seguridad perimetral y herramientas de monitorización. El proyecto no solo buscaba integrar componentes técnicos, sino también plantear un escenario de trabajo en equipo, donde cada miembro asumiera roles y responsabilidades definidos, simulando así un entorno laboral real.

</details>

<details>
<summary>Motivación y objetivos generales 🔽</summary>

  La motivación principal surgió del reto de aplicar, de forma práctica y autodidacta, tecnologías que habíamos estudiado  de forma teórico-práctica: virtualización con Proxmox, gestión de redes con pfSense, despliegue de servicios con Docker, y desarrollo de una herramienta de linux propia para monitorización. Queríamos afrontar el desafío de integrar todos estos elementos en un proyecto funcional, con el objetivo general de demostrar cómo es posible ofrecer a una empresa un producto de monitoreo de red completo y escalable, acompañado de una infraestructura segura y robusta.

  Entre los objetivos generales destacamos:

  - Diseñar y desplegar una red empresarial simulada en un entorno virtualizado.

  - Configurar servicios de red esenciales: DNS, DHCP, firewall, NAT y web.

  - Implementar un servidor Docker que albergue la página web corporativa.

  - Desarrollar una herramienta de linux de monitoreo de red basada en Python y SNMP.

  - Integrar herramientas como Grafana, Prometheus y Suricata para análisis avanzado.

  - Simular un escenario realista con estaciones de trabajo y tráfico de red.

  - Documentar y automatizar configuraciones (por ejemplo, con Docker Compose).

  - (No cumplido) Desplegar un sistema completo de alertas automáticas basadas en métricas.

  - (No cumplido) Integrar pruebas de rendimiento y stress para evaluar la robustez del entorno.

  - (No cumplido) Diseñar una demo comercial completa para clientes ficticios, incluyendo reportes personalizados.

  Aunque no todos los objetivos pudieron cumplirse por limitaciones de tiempo y alcance, planteamos desde el inicio un diseño escalable, que permita añadir futuras funcionalidades sin necesidad de reestructurar el sistema base.

</details>

<details>
<summary>Breve descripción del entrono 🔽</summary>

  El entorno del proyecto se despliega sobre un servidor físico en clase que actúa como host de Proxmox. Desde allí, hemos configurado varias máquinas virtuales, destacando pfSense, que cumple funciones de router, firewall, DHCP y DNS para el resto del entorno. El sistema se divide en dos grandes redes:

  Red genérica, donde un servidor Docker aloja una página web estática en Nginx.

  Red empresarial simulada, que incluye un servidor de servicios Docker Compose (Grafana, Prometheus, Suricata) y varias máquinas Alpine Linux que representan a los trabajadores.

  El entorno se conecta a la red del centro a través del servidor físico, utilizando Cloudflare para gestionar el dominio externo de la página web, asegurando así que el entorno sea accesible tanto desde dentro como desde fuera, simulando un escenario real de empresa con servicios públicos y privados. Todo el diseño fue concebido para poder extenderse fácilmente, añadiendo nuevas máquinas, servicios y redes según las necesidades del proyecto.

</details>

---

## 🧩 CORE

El núcleo del proyecto (core) está formado por la combinación de la herramienta de linux propia de monitorización (desarrollada en Python y SNMP) junto con toda la infraestructura de red simulada montada sobre Proxmox, que reproduce el entorno de una empresa real. Este núcleo no es solo la app en sí, sino todo el ecosistema: redes, servidores, firewalls, balanceadores, sistemas de monitorización y seguridad. La idea clave del core es mostrar la capacidad del equipo para integrar múltiples tecnologías en un sistema funcional, seguro y preparado para escalar, cumpliendo tanto los requisitos mínimos como añadiendo extras significativos que enriquecen el proyecto.

## 🎯 OBJETIVOS Y FUNCIONALIDADES
<details>
<summary>Objetivos generales 🔽</summary>

  - Diseñar y desplegar una infraestructura empresarial virtualizada sobre Proxmox.

  - Integrar pfSense como firewall, DHCP, DNS, router y punto de control de la red.

  - Desarrollar y poner en marcha una herramienta de linux propia de monitorización de red.

  - Documentar todo el proyecto, incluyendo diagramas, mapas físicos y lógicos, configuraciones y - anexos.

  - Incorporar prácticas de backup regulares para garantizar la recuperación ante fallos.

  - Cumplir todos los requisitos mínimos y, en la medida de lo posible, alcanzar requisitos extra.

  - (No cumplido) Garantizar la seguridad de los datos mediante cifrado y sistemas de protección.

  - (No cumplido) Desplegar un entorno de alta disponibilidad o clustering.

  - (No cumplido) Implementar un sistema avanzado de alertas automatizadas en tiempo real.

</details>

<details>
<summary>Objetivos específicos 🔽</summary>

  - Configurar reglas avanzadas en pfSense para el control del tráfico y el filtrado por firewall.

  - Orquestar los contenedores necesarios usando Docker y Docker Compose.

  - Configurar un servidor DNS (con Pi-hole) que gestione nombres internos.

  - Desarrollar gráficas de monitorización con Grafana y recopilar métricas con Prometheus.

  - Implementar IDS/IPS usando Suricata para la detección de posibles amenazas.

  - Realizar backups periódicos: de bases de datos, de sistemas completos (Proxmox) y mediante rsync.

  - Integrar el entorno con Cloudflare para gestionar dominios públicos y proteger el acceso externo.

  - Proteger los datos en tránsito y en reposo mediante cifrado y buenas prácticas de seguridad.

  - (Pendiente) Añadir un clúster de alta disponibilidad en Proxmox para asegurar tolerancia a fallos.

  - (Pendiente) Integrar Firebase o servicios externos para mejorar la interacción con la app.

</details>

<details>
<summary>Funcionalidades principales 🔽</summary>

  ✅ Gestión completa de redes virtuales y físicas

  - Configuración y administración de redes virtuales en Proxmox.

  - Máquinas virtuales con múltiples interfaces de red (WAN, LAN, red simulada).

  - Integración de red virtual con entorno físico, simulando una empresa real.

  ✅ Firewall y control de red

  - Configuración de pfSense con tres interfaces: WAN, LAN, red simulada.

  - Reglas avanzadas de firewall en pfSense (iptables/pfSense).

  - Segmentación de red, control de acceso y redireccionamiento de tráfico.

  ✅ Servicios centrales (pfSense)

  - DHCP centralizado para asignación de IPs en toda la red.

  - DNS primario (usando Pi-hole y pfSense) para la resolución de nombres internos.

  ✅ Monitorización avanzada

  - Configuración remota y recolección de datos a través de SNMP.

  - Monitoreo de uso de CPU, memoria, ancho de banda, direcciones IP, sistemas operativos, nombres de host, direcciones MAC.

  - Clasificación de dispositivos por tipo (switches, routers, PCs, servidores, etc.).

  ✅ Herramienta de linux propia

  - Página web desarrollada y desplegada en contenedor Docker.

  - Interfaz gráfica para visualizar en tiempo real el estado de la red.

  ✅ Red simulada adicional

  - Red interna separada con su propio servidor dedicado.

  - Servicios internos activos: DHCP, LDAP, FTP en esa red simulada.

  ✅ Copias de seguridad y seguridad de datos

  - Copias de seguridad periódicas programadas (cron, rsync, volcados de bases de datos).

  - Backup completo de máquinas virtuales en Proxmox.

  - Cifrado de datos en bases de datos y comunicaciones seguras.

  ✅ Documentación

  - Diagrama físico y lógico de la red.

  - Diagrama de datos y navegabilidad de la aplicación.

  - Identificación de roles de usuarios (incluyendo rol de víctima si aplica).

  - Documentación técnica detallada de todas las tecnologías, versiones y configuraciones.

</details>

<details>
<summary>Funcionalidades Extra 🔽</summary>

  ⭐ IDS/IPS (Suricata)

  - Implementación de sistema de detección y prevención de intrusiones para analizar el tráfico.

  ⭐ Grafana + Prometheus

  - Monitorización visual avanzada con paneles y métricas gráficas.

  ⭐ Proxy inverso (nginx)

  - Gestión del tráfico web y de los servicios internos a través de un proxy reverse.

  ⭐ VPN (OpenVPN)

  - Acceso remoto seguro al entorno virtualizado.

  ⭐ Backup en Proxmox (nivel máquina virtual)

  - No solo backups de datos, sino de snapshots completos de las máquinas virtuales.

</details>

<details>
<summary>Alcance del proyecto 🔽</summary>

  El proyecto se planteó desde el inicio como una solución integral de monitorización y seguridad de red que pudiera venderse a pequeñas y medianas empresas. El objetivo no era solo montar una red funcional, sino simular un entorno real que demostrara la validez de nuestra herramienta de linux dentro de un ecosistema profesional. Para ello, decidimos montar toda la infraestructura sobre Proxmox, lo que nos permitió trabajar con redes virtualizadas, máquinas separadas, backups automatizados y servicios independientes.

  El alcance incluía:
  - ✅ Montar toda la infraestructura simulada en Proxmox.
  - ✅ Desplegar servicios esenciales como DNS, DHCP, firewall, servidores web, monitorización.
  - ✅ Desarrollar y presentar una aplicación propia que recoja y muestre datos de red.
  - ✅ Incorporar prácticas de seguridad y de backup.
  - ✅ Documentar exhaustivamente el proyecto, incluyendo diagramas, roles de usuario, tecnologías y configuraciones.

  Sin embargo, por limitaciones de tiempo y recursos, no se llegó a cubrir la implementación de algunas funcionalidades avanzadas como el clustering en Proxmox, la integración de sistemas externos como Firebase o el despliegue de alertas inteligentes. Aun así, el proyecto fue diseñado pensando en la escalabilidad: es decir, todo el núcleo está preparado para crecer y añadir nuevas funcionalidades en el futuro sin necesidad de rediseñar la arquitectura principal. Esto asegura que el trabajo hecho no solo cumple con los objetivos actuales, sino que sienta una base sólida para ampliaciones posteriores.

</details>

## 🌐 HERRAMIENTA DE LINUX

<details>
<summary>Explicación 🔽</summary>
<br>
Esta herramienta de línea de comandos en Python permite monitorear dispositivos en red a través del protocolo SNMP (Simple Network Management Protocol). Está diseñada para funcionar en sistemas Linux y utiliza snmpget y snmpwalk de la suite net-snmp.
<br><br>
🔧 Funcionalidades principales:<br>
  
- Detección de dispositivos SNMP: Consulta información básica como nombre, descripción del sistema, ubicación, uptime y contacto del administrador.
- Exploración de interfaces de red: Muestra el estado, nombre y dirección MAC de cada interfaz encontrada.
- Presentación amigable: Usa la librería rich para mostrar los datos en tablas con colores y estilos legibles.
- Soporte para múltiples IPs: Puedes especificar una o varias direcciones IP para escanear simultáneamente.
<br>
Modos de operación:

- dispositivos: Muestra solo información del sistema de cada IP.
- interfaces: Muestra únicamente las interfaces de red.
- todo: Muestra ambos conjuntos de información.

<br>
🛠️ Requisitos:

- Python 3.x
- Paquetes: rich
- Dependencias del sistema: snmpget, snmpwalk (instalable con sudo apt install snmp)
<br>
</details>

<details>
<summary>Demo 🔽</summary>



</details>

## 🔨 ARQUITECTURA

<details>
<summary>Explicación 🔽</summary>

  La arquitectura del proyecto sigue un modelo cliente-servidor segmentado en varias redes, pensado para ofrecer seguridad, escalabilidad y resiliencia.

  Se ha desplegado sobre una infraestructura basada en Proxmox VE 8.2.2 como hipervisor principal, que alberga tanto máquinas virtuales como contenedores, organizando los servicios en capas según su propósito.

  Infraestructura general

  - Proxmox VE (hipervisor): Actúa como núcleo del entorno virtualizado, gestionando máquinas virtuales, redes virtuales y snapshots para backup.

  - pfSense (firewall y gateway principal): Gestiona el enrutamiento entre las redes, aplicando políticas de firewall, reglas de NAT, y ofreciendo servicios de DHCP y DNS.

  - Servidor de Backup (Ubuntu Server 22.04.2): Encargado de realizar y almacenar backups periódicos, incluyendo volcados de bases de datos y snapshots completos de las VMs.

  - Servidor Docker (Ubuntu Server 22.04.2): Aloja los contenedores de la herramienta de linux principal y servicios asociados.

  - Cloudflare (servicio externo): Proporciona capa adicional de seguridad web mediante túnel seguro, optimización de tráfico y mitigación de ataques DDoS.


  Este diseño nos permite separar funciones críticas (como firewalling, backup, y aplicación) evitando puntos únicos de fallo y facilitando futuras ampliaciones del entorno.

</details>

<details>
<summary>Diagrama de red 🔽</summary>

  ![Esquemaredmain](img/DiagramaRed.png)

</details>

<details>
<summary>Componentes principales 🔽</summary>

  - Proxmox VE → Hipervisor para gestionar máquinas virtuales, redes y almacenamiento.

  - pfSense → Firewall, NAT, servidor DHCP y DNS, punto central de control de tráfico.

  - Servidor de backup → Responsable de las copias de seguridad y restauración.

  - Servidor Docker → Despliegue de herramientas de linux y servicios internos en contenedores.

  - Cloudflare → Seguridad adicional, protección perimetral y optimización de servicios web.

</details>

<details>
<summary>Breve explicación de cómo se interconectan 🔽</summary>

  La comunicación entre los componentes sigue una estructura organizada:

  - pfSense interconecta las tres redes: WAN (salida a Internet), LAN (servicios internos) y la red simulada (entorno aislado).

  - Todo el tráfico, tanto interno como externo, pasa por pfSense, donde se aplican las reglas de firewall y redireccionamiento.

  - Proxmox administra las máquinas virtuales, incluyendo el servidor de backup y el servidor Docker, permitiendo gestionar snapshots y backup de todo el entorno.

  - Docker comunica con el exterior mediante el proxy reverso configurado, protegido además por Cloudflare, mientras que internamente conecta con las bases de datos y servicios simulados.

  - La red simulada contiene su propio servidor con servicios como DHCP, LDAP y FTP, separado de la LAN principal pero accesible según reglas configuradas.

  - El servidor de backup recibe datos desde las bases de datos y sistemas, programando sincronizaciones periódicas.

</details>

<details>
<summary>Tabla de arquitectura de los sistemas 🔽</summary>

  | Máquina       | S.O                  | Almacenamiento / Memoria|    Servicio    | 
  |---------------|----------------------|-------------------------|----------------|
  | **Proxmox**   |Proxmox-VE 8.2.2      | 93Gb / 8Gb              |   Hypervisor   |
  | **PfSense**   |FreeBSD 1.0.0         | 25Gb / 4Gb              |  DHCP+DNS+Firewall |
  | **Backup**    |Ubuntu server 22.04.2 | 20Gb / 4Gb              |     Backup     |
  | **Docker**    |Ubuntu server 22.04.2 | 20Gb / 2Gb              |     Hosting    |

</details>

## 📝  ORGANIZACIÓN Y ROLES DEL EQUIPO
<details>
  <summary>Organización 🔽</summary>

  Hemos decidido respetar los intereses y la motivación de cada miembro del equipo en cuanto a los aspectos de nuestro proyecto en los que desean trabajar. De este modo, todos podemos aprender más sobre las áreas en las que consideramos que podemos enfocarnos como futuras carreras profesionales. No obstante, siempre se garantiza la colaboración y el apoyo entre los integrantes del equipo en caso de no cumplir con los objetivos dentro de los plazos establecidos. 
  
  Al final de cada clase se pondrá en común el trabajo de cada integrante, con el objetivo de que todas las personas en todo momento sepan que se ha hecho ese día y si algún día hay una baja, que se pueda seguir trabajando con normalidad.

</details>

<details>
  <summary>Roles 🔽</summary> 
  
  - David - Programación, documetación (GitHub)
  - Miquel - Sistemas, Redes, documentación (GitHub)
  - Tim - Sistemas, Redes, documentación (GitHub)

</details>

## 💻 TECNOLOGÍAS A UTILIZAR 
<details>
<summary>Front end 🔽</summary>

  - HTML
  - CSS
  - Bootstrap
  - Colores a utilizar en el front-end: pendientes a elegir

</details>

<details>
<summary>Back end 🔽</summary>

 - Python
 - SNMP

</details>

<details>
<summary>Software 🔽</summary>

  - Visual Studio Code
  - Trello
  - GitHub
  - Cloudflare
  - Pi-hole
  - Nginx

</details>

---

## 🏁 CONCLUSIONES DEL PROYECTO
  Tras varias semanas de trabajo, hemos logrado desarrollar un entorno de red virtualizado completo, integrando diferentes tecnologías y servicios que cumplen tanto los requisitos mínimos como parte de los requisitos extra del proyecto.

  El diseño y despliegue de la infraestructura sobre Proxmox VE nos ha permitido experimentar de forma práctica con conceptos como la gestión de hipervisores, la configuración de redes virtuales, el despliegue de servicios en contenedores Docker y la administración de sistemas firewall mediante pfSense.

<details>
<summary>🏆 Hemos conseguido 🔽</summary>

  - ✅ Configurar una red segmentada que separa entornos críticos, asegurando mayor seguridad.
  - ✅ Implementar servicios esenciales como DHCP, DNS, NAT y firewall, garantizando conectividad controlada.
  - ✅ Desplegar una herramienta de linux funcional en contenedores Docker, protegida por proxy reverso y capa adicional con Cloudflare.
  - ✅ Configurar backups periódicos (incluyendo snapshots en Proxmox) para asegurar la resiliencia de datos.
  - ✅ Simular una red secundaria aislada con sus propios servicios (LDAP, FTP, DHCP), demostrando conocimientos avanzados en entornos multi-red.
  - ✅ Documentar cuidadosamente cada componente, versión y configuración utilizada.

</details>

<details>
<summary>📊 Aprendizajes clave  🔽</summary>

  El proyecto ha supuesto un reto significativo, ya que nos enfrentamos a tecnologías que no habíamos trabajado en profundidad previamente.

  Hemos reforzado habilidades de:

  - Configuración de redes avanzadas (subredes, NAT, reglas de firewall).

  - Despliegue automatizado de servicios (Docker, scripts, crontab).

  - Documentación técnica profesional.

  - Trabajo en equipo, dividiendo tareas de forma eficiente y colaborando en la resolución de problemas.

</details>

<details>
<summary>⚠️ Objetivos no cumplidos o pendientes  🔽</summary>

  Si bien se lograron cumplir la mayoría de objetivos, hubo algunos aspectos que quedaron parcialmente implementados o en desarrollo:

  - ❌ Integración completa de herramientas de monitorización avanzada como Grafana + Prometheus.
  - ❌ Implementación final de IDS/IPS (aunque se investigó Suricata, no se llegó a integrar del todo).
  - ❌ Optimización de las configuraciones de rendimiento y seguridad a nivel de clúster Proxmox (por tiempo).
  - ❌ Automatización total de despliegues (quedaron scripts sueltos no integrados en un pipeline).

</details>

<details>
<summary>🔭 Proyección futura 🔽</summary>

  Este proyecto nos ha abierto la puerta a nuevas líneas de trabajo que consideramos valiosas para el futuro, como:

  - Completar la integración de sistemas de monitorización avanzados.

  - Explorar configuraciones de clúster en Proxmox para alta disponibilidad.

  - Refinar el enfoque de seguridad, aplicando políticas más estrictas (p. ej. IDS/IPS, escaneo de vulnerabilidades).

  - Profundizar en la automatización de despliegues para minimizar intervención manual.

  En resumen, hemos superado con éxito muchos de los retos planteados, demostrando capacidad para aprender y aplicar tecnologías nuevas de forma autodidacta, trabajando de manera colaborativa y resolviendo problemas de arquitectura, redes, sistemas y ciberseguridad. Este proyecto nos ha dejado aprendizajes que podremos aplicar tanto en futuros desarrollos académicos como en proyectos reales del entorno profesional.

</details>

---

## ⚙️ CONFIGURACIONES

### 🐳 DOCKER
<details>
<summary>Introducción 🔽</summary>

  En este proyecto vamos a implementar Docker, una plataforma de contenedorización que permite crear, desplegar y ejecutar herramientas de linux en contenedores. Distingue por su portabilidad y consistencia, esto significa que nos permite trabajar desde cualquier sitio desplegando la misma imagen en otro servidor, nube, etc. Además nos proporciona un aislamiento de los servicios, en caso de tener algún fallo en un contenedor, el servicio afectado será únicamente el que se almacenaba dentro de este contenedor. Por último, los contenedores docker comparten el mismo kernel del sistema operativo, lo que permite reducir el consumo de RAM, CPU y memória física, optimizando el tiempo del arranque, desarrollo y apague de los servicios.

</details>

<details>
<summary>Información básica 🔽</summary>

  ¿Qué son los contenedores de docker?
    - La función principal de los contenedores Docker es desarrollar, enviar y ejecutar cualquier aplicación en cualquier sistema, constituyéndose así como una alternativa flexible y capaz de ahorrar recursos frente a la emulación de componentes de hardware basada en máquinas virtuales (VM).

  ¿Qué diferencias hay entre los contenedores de docker y los lxc?
    - LXC: es un tipo de contenedor de sistema lo que significa que todos los contenedores creados con LXC necesitan un sistema operativo propio para funcionar, podemos tener en un solo contenedor diferentes aplicaciones, más parecido a una máquina virtual, es neutral en cuanto al sistema de archivos, permite guardar datos dentro o fuera del contenedor, facilita la construcción de pilas acopladas o compuestas.
    - Docker: utiliza el sistema operativo del sistema anfitrión (kernel), solo un contenedor para un servicio, es más ligero y modular, se basa en capas de solo lectura mediante AUFS o DeviceMapper, sus instancias son efímeras, y los datos persistentes deben almacenarse en bind mounts o volúmenes de datos.

  ¿Cuál es la diferencia entre una imagen y un contenedor en docker?
    - Imagen: una imagen es una plantilla fija que contiene el sistema de archivos y la configuración necesarios para ejecutar una aplicación. Si se necesita realizar cambios, hay que crear una nueva imagen a partir del contenedor creado a partir de la imagen inicial.  
    - Contenedor: un contenedor es una instancia de ejecución de una imagen, aunque la imagen contenga todo lo necesario para ejecutar una aplicación no podrá ser ejecutada sin un contenedor. El contenedor es modificable pero, los cambios que se implementan no afectan a la imagen base. Un contenedor puede ser eliminado o detenido sin afectar la imagen. 

  ¿Qué sucede con los datos cuando un contenedor se elimina?
    -  Cuando un contenedor es eliminado todos los datos no persistentes se borran si no se usan volúmenes o bind mounts.
    -  Volúmenes:  se almacenan fuera del sistema de archivos del contenedor y pueden ser reutilizados por otros contenedores.
    -  Bind Mounts: permite acceder y modificar archivos dentro y fuera del contenedor. 

  ¿Cuáles son las ventajas de utilizar contenedores de docker?
    - Entre todas las ventajas que proporciona el uso de contenedores de docker destacan las siguientes: la ejecución en cualquier sistema que tenga instalado el docker, el arranque más rápido, menor consumo de los recursos, ejecución independiente de cada contenedor, facilidad de desarrollo y despliegue.

  ¿Qué tipo de aplicaciones y servicios se pueden desplegar con docker?
    - Docker es muy versátil a la hora del despiegue de las aplicaciones y servicios, puede desplegar aplicaciones web, APIs, BBDD y almacenamiento (MySQL, MongoDB, Elasticsearch, etc.), sistemas de mensajería y colas de trabajo (RabbitMQ, NATS, etc.), entornos de desarrollo y testing (Jenkins, GitLab CI/CD...), servicios de monitoreo y logging (Grafana, Prometheus, etc.), creación de arquitecturas basadas en microservicios utilizando Docker Compose o Kubernetes, aplicaciones de Inteligencia Artificial y Big Data (Jupyter Notebooks, Spark, etc.), VPNs y redes privadas (WireGuard, OpenVPN, Pi-hole, etc.), aplicaciones empresariales y ERP/CRM (WordPress, Magento, etc.)

  ¿Qué otros tipos de contenedores existen además de Docker?
    - A parte de contenedores LXC y Docker existen otros contenedores para unos u otros propósitos: Podman (alternativa a Docker, utiliza los mismos comandos y no necesita un daemon en segundo plano), CRI-O (más optimizado para Kubernetes), Singularity (usado en entornos científicos), Kata Containers (combina virtualización ligera con seguridad similar de las VMs), Firecracker (contenedores livianos, elaborados por Amazon).

  **Webgrafía** [Dockerdocs](https://docs.docker.com/) [DockervsLXC](https://www.upguard.com/blog/docker-vs-lxc) [Codeandcoke](https://despliegue.codeandcoke.com/apuntes:docker)

</details>

<details>
<summary>Despliegue de herramienta de linux 🔽</summary>

  Para el despliegue de la herramienta de linux vamos a utilizar una herramienta de orquestación de los contenedores dentro del mismo cliente, **docker-compose**.  

  Para descargar **docker-compose** necesitamos tener instalada la herramienta de Docker en sistema que vamos a trabajar. Una vez descargadas ambas herramientas comprimimos todos los archivos de nuestra web almacenada en un directorio en windows y los pasamos a la nuestra máquina especificando el nombre del **.zip**, el usuario y la ip de nuestra máquina. 

  Una vez que tengamos nuestros archivos en nuestra máquina virtual, los descomprimimos y organizamos la estructura de directorios de la web a nuestro gusto. Una posible opción sería crear una carpeta general con el nombre del proyecto y, dentro de ella, cuatro carpetas para los diferentes servicios, en nuestro caso son: nginx, web, mysql y sql. 

  Pasamos a la configuración del archivo más importante de todos, el ```docker-compose.yml``` dentro del cuál definiremos los contenedores que se van a desplegar y que dependencias van a tener entre ellos. 
  Ejemplo de definición del servicio de base de datos:

  ```

  # MySQL database service
  db:
    image: mysql
    container_name: miDB
    ports:
      - "3306:3306"
    environment:
      MYSQL_ROOT_PASSWORD: 1234
    volumes:
      - ./mysql:/var/lib/mysql
      - ./sql:/db
    networks:
      - netweb

  ```

  Finalmente añadimos el archivo de configuración **default.conf** dentro de la carpeta de nginx.
  
  ```
  # comandos usados

  sudo apt install docker-compose                        # instalación del servicio
  sudo scp nombre_archivo.zip usuario@ip:.               # comprimir todo en .zip y pasar al sistema de trabajo
  sudo unzip nombre_archivo.zip                          # descomprimimos dentro de máquina con docker
  sudo nano docker-compose.yml                           # modificación del archivo de definición de los servicios
  docker-compose up                                      # despliegue de la aplicación
  docker-compose down                                    # detener la ejecución de los contenedores
  docker-compose ps                                      # listar los servicios desplegados y contenedores asociados

  ```
    
  **Webgrafía** [Adictosaltrabajo](https://adictosaltrabajo.com/2022/12/19/despliegue-de-aplicaciones-con-docker-compose/)

</details>

### 🧱 PFSENSE
<details>
<summary>Introducción 🔽</summary>

  El software pfSense es una distribución personalizada, libre y de código abierto de FreeBSD, diseñada específicamente para usarse como cortafuegos y enrutador, que se administra completamente a través de una interfaz web. Además de ser una plataforma de cortafuegos y enrutamiento potente y flexible, incluye una larga lista de características relacionadas y un sistema de paquetes que permite una mayor capacidad de expansión sin agregarle volumen ni posibles vulnerabilidades de seguridad a la distribución base.

</details>

<details>
<summary>Configuración + Portforwarding 🔽</summary>

  [pfSense](documentos/pfSense.pdf)

  **Webgrafía** [pfSense](https://www.pfsense.org/)

</details>

### 💾 BACKUP
<details>
<summary>Introducción 🔽</summary>

  En el mundo que vivimos la información se ha convertido en uno de los recursos más importantes la pérdida del cuál puede tener consecuencias muy graves para una empresa. Un backup o una copia de seguridad permite almacenar un respaldo de los datos originales en otro dispositivo o ubicación para recuperarlos en caso de pérdida o corrupción de la versión original. 

  El sistema de copias de seguridad de nuestro proyecto es desplegado en la máquina del trabajador, cargando el script en memoria (/usr/local/bin). El script deberá de tener los permisos de ejecución para poder utilizarlo de manera apropiada. Se puede indicar de manera manual el tipo de copia que se desea hacer sea incremental o completa, está ajustado a las necesidades del usuario para que pueda tener una copia lo más reciente posible independientemente de los horarios del backup automantizado.

</details>

<details>
<summary>Pasos para generar backup manualmente 🔽</summary>

  Fase preparación prévia:
    - En local el usuario que efectúe el backup de manera manual deberá de tener permisos sobre **/ [sudo chown {usuario} /]**.
    - En remoto hemos creado un usuario **admin_backup** en la máquina servidor de backup que tiene permisos sobre **/ [sudo chown admin_backup /]**. Si no se han pasado las claves pedirá contraseña (password) **[ssh key-gen -t rsa] [ssh-copy-id admin_backup@100.77.20.47]**. 

</details>

<details>
<summary>Instrucciones de copia de seguridad manual 🔽</summary>

  Para crear la estructura de carpetas donde se guardará el backup por primera vez escribimos **backup estructura**. Esta sintaxis crea una carpeta en local para almacenar los comprimidos, además hace lo mismo de manera remota en máquina aparte. Así mismo aseguramos que el backup manual no falle y encuentre las carpetas hechas. 

  Salida esperada: 

  ![BKPestructura](img/backup_estructura.png)

  Una vez tengamos nuestra estructura de carpetas necesitamos introducir la sintaxis **backup [parametro 1]** para realizar la copia de seguridad. El **parámetro 1** es la ruta al directorio a realizar la copia manual. 

  Salida esperada comprimirá la ruta indicada por el usuario en la ruta local y remota:

  ![BKPexistente](img/bkp_esctructura_existente.png)

  Resultados del backup en local:

  ![BKPlocal](img/resultado_local.png)

  Y en remoto:

  ![BKPlocal](img/resultado_remoto.png)


</details>

<details>
<summary>Instrucciones restore sobre la copia de seguridad manual 🔽</summary>

  Para realizar un restore de una copia de seguridad hay que utilizar la siguiente sintaxis: 
    - **restore [parámetro 1] [parámetro 2]**
    - Donde **parámetro 1** es la fecha del backup que se quiera recuperar en formato (año-mes-día).
    - Y **parámetro 2** es la ruta a donde se quiera traer la copia.

  Salida esperada:

  ![RestoreParametros](img/param_restore.png)

  Resultado en ambas máquinas:

  ![RestoreResultados](img/resultado_restore.png)

</details>

## ⭐ EXTRAS

Este apartado recopila configuraciones y documentación de servicios que no fueron implementados en nuestro proyecto, pero que resultan relevantes y merecen atención, investigación y el tiempo dedicado a su análisis.

<details>
  <summary> 💬 Ejabberd & Pidgin 🔽</summary>

[EjabberdPidgin](documentos/Pidgin_y_ejabberd.pdf)
  
</details>

<details> 
  <summary> :unlock: OpenVPN 🔽</summary>

[OpenVpn](documentos/Openvpn.pdf)

</details>

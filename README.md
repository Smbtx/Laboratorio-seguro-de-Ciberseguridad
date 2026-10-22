**CIBERSEGURIDAD**

**Modulo 2 – Mi primer laboratorio seguro de ciberseguridad**

**Alumno: Gomez David Gabriel.**

**Comisión: 90870**



**Reporte Técnico de Configuración de Laboratorio**

Checkpoint: Mi primer laboratorio seguro de ciberseguridad

**Introducción**

El objetivo de esta actividad es crear y configurar una Máquina Virtual (VM) destinada a prácticas de ciberseguridad, aplicando medidas básicas de seguridad antes de comenzar a utilizarla para actividades de laboratorio.

La configuración busca establecer un entorno controlado y separado del sistema principal, utilizando una cuenta de usuario con privilegios limitados, manteniendo el sistema operativo actualizado y creando una instantánea inicial que permita recuperar el estado seguro de la máquina en caso de que una práctica futura provoque algún inconveniente.

Para este laboratorio se utilizó VirtualBox y una máquina virtual con sistema operativo Windows.



**Fundación: VirtualBox y red aislada**

**Configuración de red**

Antes de comenzar las prácticas se configuró la interfaz de red de la máquina virtual utilizando el modo NAT (Network Address Translation).

**Evidencia:**
![1 Prueba Windows RED NAT](Capturas/1%20Prueba%20Windows%20RED%20NAT.png)

La configuración se realizó desde: VirtualBox → Configuración → Red → Adaptador 1 → Conectado a: NAT

Justificación

Se seleccionó el modo NAT porque permite que la máquina virtual tenga acceso a Internet para realizar tareas como descargar actualizaciones y herramientas, sin exponerla directamente como un dispositivo independiente dentro de la red local.

De esta manera, la máquina virtual queda en un entorno más controlado que utilizando el modo Puente (Bridged Adapter), donde la VM podría aparecer en la red local como otro equipo.

Esta configuración constituye una primera medida de aislamiento del laboratorio y reduce la exposición innecesaria del sistema Host frente a las actividades que se realizarán posteriormente dentro de la máquina virtual.

Capa Windows: usuarios y actualizaciones

Creación de un usuario estándar

Como medida de seguridad se creó un usuario destinado a las prácticas con permisos estándar, separado de la cuenta administrativa.

Evidencia:
![2 Prueba Windows Usuario estandar](Capturas/2%20Prueba%20Windows%20Usuario%20estandar.png)

El objetivo de utilizar una cuenta sin privilegios administrativos para las actividades habituales es aplicar el principio de mínimo privilegio.

Este principio establece que cada usuario debería disponer únicamente de los permisos necesarios para realizar sus tareas. De esta forma, si una aplicación o actividad realizada durante una práctica se ve comprometida, se limita el nivel de acceso que podría obtener.

La cuenta administrativa queda reservada para tareas que realmente requieran privilegios elevados.



**Actualización del sistema operativo**

Se verificó el estado de actualización del sistema operativo mediante Windows Update.

**Evidencia:**
![4 prueba windows actualizado](Capturas/4%20prueba%20windows%20actualizado.png)


Mantener el sistema operativo actualizado es una medida fundamental de seguridad, ya que las actualizaciones pueden incluir correcciones de vulnerabilidades, errores y problemas de seguridad detectados por el fabricante.

Antes de utilizar la máquina virtual para prácticas de ciberseguridad, se considera importante partir de un sistema actualizado para reducir la exposición a vulnerabilidades conocidas.



**Red de seguridad: Snapshot inicial**

Una vez finalizada la configuración inicial y aplicadas las medidas básicas de seguridad, se creó una instantánea de la máquina virtual utilizando VirtualBox.

El Snapshot fue denominado:

Clean Install - Hardening applied

**Evidencia:**
![3 prueba Windows snapshot](Capturas/3%20prueba%20Windows%20snapshot.png)


**Usuario estándar en Kali Linux**

En Linux se crea un usuario estándar para utilizar en el día a día, sin permisos de administrador (Root). Esto evita modificar archivos del sistema por error y limita los daños si alguna herramienta o programa se ve comprometido; solo se usa el permiso de super usuario con sudo cuando sea necesario para tareas de configuración o actualización.

**Evidencia:**
![7 Prueba Linux Usuario limitado](Capturas/7%20Prueba%20Linux%20Usuario%20limitado.png)


Descripción: Usuario destinado a las prácticas configurado con permisos estándar.

Capa Linux: permisos y gestión

Comprobación de permisos mediante ls -l

Como parte de la práctica se utilizó la terminal para crear un archivo y posteriormente visualizar sus permisos mediante el comando: ls -l

**Evidencia:**
![6 prueba Linux permisos](Capturas/6%20prueba%20Linux%20permisos.png)


El comando ls -l permite visualizar información detallada sobre los archivos y directorios, incluyendo sus permisos, propietario y grupo.

Los permisos permiten determinar qué usuarios pueden leer, modificar o ejecutar un determinado archivo.

Esta comprobación permite familiarizarse con uno de los mecanismos fundamentales de seguridad de los sistemas Linux: el control de acceso basado en permisos.

Nota: esta evidencia corresponde a la máquina Linux utilizada como parte de las prácticas del laboratorio.

Gestión de actualizaciones mediante APT

También se utilizó la terminal para consultar la disponibilidad de actualizaciones de los paquetes mediante:

sudo apt update

**Evidencia:**
![8 Prueba Linux actualizado](Capturas/8%20Prueba%20Linux%20actualizado.png)


El comando sudo apt update actualiza la información disponible sobre los paquetes de los repositorios configurados.

El uso de sudo permite ejecutar la operación con privilegios elevados de manera puntual, sin necesidad de trabajar permanentemente con la cuenta root.

Esta práctica permite reforzar el concepto de utilizar privilegios administrativos únicamente cuando son necesarios.



**Red de seguridad: Snapshot inicial**

Una vez finalizada la configuración inicial y aplicadas las medidas básicas de seguridad, se creó una instantánea de la máquina virtual utilizando VirtualBox.

El Snapshot fue denominado:

Clean Install - Hardening applied

**Evidencia:**
![9 Prueba Linux Snapshot](Capturas/9%20Prueba%20Linux%20Snapshot.png)


La instantánea funciona como un punto de recuperación del laboratorio. Si durante una práctica futura se modifica accidentalmente la configuración, se instala una herramienta problemática o el sistema queda en un estado no deseado, será posible regresar al estado previamente guardado.

Por este motivo, el Snapshot representa una medida importante para mantener un entorno de pruebas controlado y facilitar la recuperación del laboratorio.



**Medidas de seguridad aplicadas**

A través de la configuración realizada se implementaron diferentes medidas básicas de seguridad:

Medida Objetivo

Red NAT Reducir la exposición directa de la máquina virtual en la red local

Usuario estándar Aplicar el principio de mínimo privilegio

Actualizaciones de Windows Mantener el sistema protegido frente a vulnerabilidades conocidas

Permisos Linux Comprender y controlar el acceso a archivos

sudo Utilizar privilegios elevados únicamente cuando sean necesarios

Snapshot Permitir la recuperación del estado seguro del laboratorio

Estas medidas no convierten a la máquina virtual en un sistema completamente seguro, pero establecen una configuración inicial adecuada para comenzar prácticas de ciberseguridad en un entorno controlado.



**CONCLUSIÓN**

La actividad permitió construir una primera máquina de prácticas aplicando diferentes capas básicas de seguridad.

La configuración de red mediante NAT proporciona un nivel inicial de aislamiento, mientras que el uso de una cuenta estándar permite aplicar el principio de mínimo privilegio. La instalación de actualizaciones contribuye a mantener el sistema actualizado y la utilización de permisos en Linux permite comprender cómo se controla el acceso a los recursos.

Finalmente, la creación de una instantánea establece un punto de recuperación que permitirá experimentar con diferentes herramientas y configuraciones durante futuras prácticas sin perder fácilmente el estado inicial del laboratorio.

De esta manera, la máquina virtual queda preparada como un entorno controlado para continuar desarrollando actividades de aprendizaje en ciberseguridad.




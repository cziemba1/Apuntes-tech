# Azure

Created: Aug 30, 2020 9:04 AM
Reviewed: No

Nube: Forma de administrar y gestionar recursos de it (computos, red y almacenamiento), que estan disponible online (no necesariamente a traves de internet). 

Principio 5(caractreristicas)-3(metodos de entrega)-2(modelos de implementacion) de Informatica en la nube:

Caracteristicas: 

1. autoservicio y autodemanda: no hay que pedir permiso para crear recursos.
2. acceso amplio y ubicuo: se puede acceder a los recursos a traves de cualquier lugar del mundo a traves de mecanismos homogeneos, basicos (navegador web, interfaz de acceso)
3. ubicacion transparente y agrupacion de recursos: la fabrica se encarga de orquestar todo 
4.  elasticidad rapida: mas o menos recursos, aunque no son ilimitados.
5. servicio medido: para cobrar, asignar gastos, conocer los recursos con fines de monitoreo.

Metodos de entrega:

1. IASS: Infraestructura como servicio, capacidad de utilizar almacenamiento y redes para implementar el software como queramos, a traves de maquinas virtuales (del sistema operativo hacia arriba)
2. PASS: Plataforma como servicio, desplegar aplicaciones sin estar viendo el sistema operativo por debajo virtuallizado, acceso ilimitado a configuraciones (servicios de hosting por ejemplo), ya viene configurado (desde la data para arriba)
3. SASS: Software como servicio, solo utilizamos el software

![Azure%208361ac811fc4440ca5362894ccc2971d/Untitled.png](Azure%208361ac811fc4440ca5362894ccc2971d/Untitled.png)

Modelos de implementacion:

1. Nube privada
2. Nube publica
3. Nube hibrida

Servicio de Nube y Azure: Podemos alquilar:

1. Potencia de proceso:

Una **máquina virtual** es una emulación de un equipo, igual que el equipo de escritorio o una portátil. Cada máquina virtual incluye un sistema operativo y hardware que se muestra al usuario como un equipo físico que ejecuta Windows o Linux, si bien dicho hardware está virtualizado.

Los **contenedores** proporcionan un entorno de ejecución aislado y coherente para las aplicaciones. Son similares a las máquinas virtuales, salvo que no requieren un sistema operativo invitado para funcionar.

En su lugar, la aplicación que queremos publicar y todas sus dependencias se empaquetan en algo llamado “contenedor”, el cual después se usa un entorno de ejecución. El contenedor, al no tener todos los archivos que una máquina virtual tiene dentro y que corresponden al sistema operativo, inicia en segundos.

El proyecto de código abierto Docker es una de las principales plataformas de administración de contenedores.

**La informática sin servidor, conocida como “Serverless”,** permite ejecutar código sin necesidad de crear, configurar o mantener un servidor ni un contenedor.

La idea principal es que la aplicación se divida en diferentes funciones que se ejecutan cuando las desencadena alguna acción. Esta acción puede ser una notificación, un horario o una petición.

1. Almacenamiento: para las maquinas virtuales, aplicaciones web, base de datos, archivos de datos, archivos para analitica
2. Redes: conectar maquinas virtuales, monitorear redes, aplicar restricciones, etc.el proveedor se encarga de todos los aspectos relacionados a redes de todos los clientes”, no obstante hay otros de los cuales debemos ocuparnos nosotros. Por ejemplo:
- Crear y configurar Redes Virtuales.
- Crear y conectar de extremo a extremo redes en la nube con una infraestructura local (conocidas como site-to-site, y point-to-site).
- Parametrizar reglas de acceso a recursos.
- Monitorear tráfico de redes.
- Aplicar reglas, restricciones y protecciones a las comunicaciones.

Azure es un servicio de informatica en la nube creado por MS, para construir, testear, desplegar y gestionar app y servicios a traves de centros de datos gestionados por MS: AI, DevOps, IpT, Management tools, Seguridad, almacenamiento.

- Inteligencia Artificial y Machine Learning.
- Analítica.
- Cómputo.
- Contenedores.
- Bases de Datos.
- Herramientas para Desarrolladores.
- DevOps.
- Identidad.
- Integración.
- Internet de las Cosas.
- Servicios de Gestión.
- Media.
- Azure Stack.
- Migración.
- Redes.
- Seguridad.
- Almacenamiento.
- Web & Servicios Móviles.

Todo esto sucede en los centros de Datos de Microsoft Azure.:

- Potencia de proceso: por ejemplo, aplicaciones web o servidores Linux.

Computo con maquinas virtuales (utilizar IaaS para nuestras app)

Estas maquinas virtuales pueden sen tanto linux como windows, se pueden escalar de 1 a 1000 instancias, se facturan por minuto, permite templates, extensiones, etc. 

Resource Group: manera de agrupar logicamente recursos(maquinas virtuales, etc)

Conjunto de disponibilidad: Agrupacion logica de 2 o mas maquinas virtuales en un mismo datacenter, permite manejar los dominos de falla y actualizacion (falla hardware y todo lo que esta en ese dominio, falla)

Zona de disponibilidad: es lo mismo pero en vez de ocurrir en un datacenter, ocurren en distitas ubicaciones fisicas dentro de una region

Quickstart center: guia para empezar con laplataforma

1. Crear recursos en azure: estas tres tabs estan en todas: basics, tag, review+create

a. Basics: Minima info para crear, Tags, Review + Create.

b. Project Details

c. Detalles intancia: nombre y region

d. Botones operar el formulario

  2.  Encontrar recursos

## **Fundamentos de Cuentas de Microsoft Azure**

- **A través de azure.com**: es la forma más rápida y fácil que tienen las organizaciones de todos los tamaños para empezar a usar Azure. Puede administrar las implementaciones y el uso de Azure, como así también obtener una factura mensual de Microsoft por los servicios usados.
- **Con la ayuda de un Partner de Microsoft**. Es un modelo para obtener facturación local en tu país. De esta manera, Azure se brindará como servicio administrado a través de un partner, quién te proporcionará el acceso y la facturación, junto con un soporte técnico básico.
- **A través de un representante directo de Microsoft**, opción pensada para organizaciones de gran tamaño o clientes que ya trabajan con la marca. A diferencia de azure.com (que requiere tarjeta de crédito), esto habilitará un tipo de contrato especial con varias ventajas al momento de necesitar varias suscripciones.

![https://azure.conosur.tech/wp-content/uploads/sites/18/2020/08/image-23.png](https://azure.conosur.tech/wp-content/uploads/sites/18/2020/08/image-23.png)

Una cuenta de facturación puede contener varias suscripciones. Por ejemplo, algunas situaciones en donde podemos decidir crear más de una suscripción son las siguientes:

- Necesidad de contar con **Entornos Independientes** para el desarrollo y las pruebas, para seguridad o para aislar los datos por motivos de cumplimiento. Esto es especialmente útil porque el control de acceso a los recursos se produce en el nivel de suscripción.
- Requerimientos de reflejar **Estructuras Organizativas** en Azure, por ejemplo para limitar un equipo de trabajo a recursos de bajo costo. Este diseño permite administrar y controlar el acceso a los recursos que los usuarios aprovisionan en cada suscripción.
- Motivos de **Facturación**. Crear suscripciones adicionales nos permite pre-cargar créditos acordados con Microsoft de facturación y así simplificar el control de gastos.
- Y, por último, existen algunos **motivos técnicos**: las suscripciones tienen Límites. Estos límites se enlazan con algunas limitaciones de hardware de Microsoft. Por ejemplo, el número máximo de circuitos ExpressRoute por cada suscripción es de 10. Esos límites se deben tener en consideración al crear suscripciones en la cuenta. Si en escenarios concretos hay que superar esos límites, es posible que se necesiten suscripciones adicionales.

## **Centros de Datos y Disponibilidad en Azure**

**Centros de Datos**

Los servicios de Azure están disponibles a través de Centros de Datos gestionados por **Microsoft**. Los mismos están conformados por edificios(cada centro ocupa 16 campos de futbol)

Existen +60 regiones anunciadas en todo el mundo, y muchas que están anunciadas como adicionales futuras. Esto representa una presencia física en 140 países.Una región es un conjunto de centros de datos implementados en un perímetro, que está definido por la latencia y conectados a través de una red regional dedicada de baja latencia.Cada región de Microsoft Azure puede tener entre 1 y 3 zonas de disponibilidad. Las zonas de disponibilidad son un concepto que representa a las ubicaciones físicas exclusivas dentro de una región de Azure.

## **SLA de Azure**

SLA significa en inglés “service level agreement”, y en español “acuerdo de nivel de servicio”. Es un acuerdo escrito entre un proveedor de servicio y su cliente con objeto de fijar el nivel acordado para la calidad de dicho servicio. Este nivel puede ser un porcentaje que representa la disponibilidad mínima:

- Por ejemplo, si el SLA es del 99%, significa que 8,76 horas al año será el máximo tiempo que un servicio podría no estar disponible.
- Para un SLA del 99,99%, significa que 0,876 horas al año será el máximo tiempo que un servicio podría no estar disponible.

En Azure el SLA varía según el servicio (algo en lo que no podemos influir) y arquitectura configurada por nosotros (en cuyo punto sí podemos influir). En este sentido, Azure puede ofrecer para muchos servicios hasta un SLA de 99,99%. Lo que hay que tener en cuenta es que a veces, ese altísimo SLA, solo se puede cumplir si tenemos configurado en nuestras cargas de trabajo zonas de disponibilidad.

## **Máquinas Virtuales en Azure**

En Microsoft Azure tenemos soporte para sistemas operativos Windows y Linux, e incluso soporte a Windows Server 2003. Puedo configurar, a través de diversas opciones, la memoria RAM asignada y la CPU que va a tener asociada.

Las máquinas virtuales en Azure permiten personalización de bajo nivel para el sistema operativo y completo control de configuraciones.

No nos olvidemos que cuando elijo trabajar sobre una máquina virtual, hay 3 responsabilidades esenciales:

- Soy el responsable de mantener el sistema operativo y sus actualizaciones.
- Soy el responsable de trabajar sobre la performance.
- Soy el responsable de monitorear el espacio de disco utilizado.

## **Componentes de una Máquina Virtual**

Una máquina virtual en Azure tiene diversos componentes:

- **Disco virtual**: el disco es el que tendrá, por ejemplo, el sistema operativo instalado. Gracias al disco virtual puedo iniciar el equipo y guardar información en forma persistente
- **Placa de red virtual**: al igual que en un equipo físico, es la que me facilitará la conexión con una o más redes.
- **Direcciones IP**: gracias a la cual podré conectarme al equipo virtual. Estas direcciones IP pueden ser privadas y públicas.
- **Grupos de seguridad de red**: que nos ayudarán a definir desde qué origenes me puedo conectar, y hacia qué destinos puedo acceder, teniendo en cuenta protocolos, puertos, etc. Los Network Security Groups son una manera ágil de gestionar los permisos de red, para una o más máquinas.

Todos estos componentes son definidos por software. No somos los responsables de mantener los componentes de bajo nivel que permiten su funcionamiento (hardware).

En Microsoft Azure podré parametrizar tres elementos fundamentales:

- **El nombre de la máquina virtual**: una vez elegido, no podrá cambiar luego de su creación.
- **El sistema operativo**: lo que ejecutará como core el equipo virtual.
- **El tamaño**: a través de tamaños pre-configurados que me brindan diversas opciones de CPU, Memoria, cantidad de discos soportados y calidad de componentes.

## **Máquinas Virtuales y Discos**

Una VM (Virtual Machine) en Azure tiene al menos dos discos:

- Uno para el sistema operativo.
- Otro temporal, para la memoria virtual. Cuando el equipo se apaga, los datos alojados en este espacio se borran. El tamaño será el doble de la memoria RAM asignada a la máquina, por lo cual ante un cambio de tamaño de memoria también cambiará el almacenamiento temporal.
- ¿Puedo agregar más discos? ¡Si! Por supuesto, pero depende del tamaño que haya elegido, podría tener limitaciones.

## Disponibilidad en Máquinas Virtuales: Introducción

Por lo general, las cargas de trabajo se distribuyen entre máquinas virtuales distintas para obtener un alto rendimiento y crear redundancia en caso de que una máquina virtual se vea afectada debido a una actualización u otro evento. Ahora bien: si solo tengo 1 máquina virtual para un rol específico (por ejemplo Web Server), ¿significa que NO tengo disponibilidad?

La respuesta es NO, no significa eso. Per se, las máquinas virtuales de Azure tienen diversos acuerdos de servicio que proporcionan un % de disponibilidad. El mínimo de ellos es 95% para equipos virtuales con disco Standard HDD Managed Disks. No obstante, probablemente querramos elevar este porcentaje (que equivale a tener un máximo de 438 horas de interrupción por año) a algo más cercano al 99.xx%.

Justamente esta lección trata sobre ello: ¿cómo hacemos esto en Azure y sus VMs? Cabe aclarar que estas secciones tratarán el tema de disponibilidad de la máquina virtual vistas como rol de aplicaciones, pero NO de la aplicación en sí misma: si la máquina virtual está encendida, pero la aplicación falla, no significa que Azure esté violando el acuerdo de disponibilidad. Estas situaciones las debe arreglar el administrador del sistema.

Por último, es importante mencionar que cuando tenemos más de 1 instancia por rol de aplicación (es decir, más de una máquina virtual para roles específicos como puede ser Web Server, o Database Server), el aspecto de red se vuelve crítico: necesitamos un balanceador. En este capítulo de máquinas virtuales haremos uso de un servicio de red llamado “Azure Load Balancer”, pero no entraremos en detalles. Lo haremos más adelante, cuando veamos redes.

Trataremos, entonces, el aspecto de disponibliidad de máquinas virtuales en base a estos lineamientos antes explicados. Hay algunas opciones que Azure proporciona para lograr alta disponibilidad:

- Conjuntos de Disponibilidad: “Availability Sets”.
- Zonas de Disponibilidad: “Availability Zones”.

![Azure%208361ac811fc4440ca5362894ccc2971d/Untitled%201.png](Azure%208361ac811fc4440ca5362894ccc2971d/Untitled%201.png)

![Azure%208361ac811fc4440ca5362894ccc2971d/Untitled%202.png](Azure%208361ac811fc4440ca5362894ccc2971d/Untitled%202.png)

![Azure%208361ac811fc4440ca5362894ccc2971d/Untitled%203.png](Azure%208361ac811fc4440ca5362894ccc2971d/Untitled%203.png)

![Azure%208361ac811fc4440ca5362894ccc2971d/Untitled%204.png](Azure%208361ac811fc4440ca5362894ccc2971d/Untitled%204.png)

![Azure%208361ac811fc4440ca5362894ccc2971d/Untitled%205.png](Azure%208361ac811fc4440ca5362894ccc2971d/Untitled%205.png)

## **SLAs en Máquinas Virtuales**

El SLA de las máquinas virtuales en Azure tienen dos componentes:

- Los recursos que utilicemos para crearla.
- La configuración realizada por los administradores.

Vamos a separar el análisis incial entre SLA para VMs con 1 sola instancia, y SLA para VMs con dos o más instancias.

## **SLA para Virtual Machines de 1 sola instancia**

Tenemos 3 distintos SLAs para cuando creamos máquinas virtuales con 1 sola instancia. ¿Qué significa esto? Supongamos que tenemos una aplicación web, y dicha aplicación web la instalamos en 1 solo servidor. Esto se considera “1 sola instancia”, y en dicho caso tengo un único punto de falla. El SLA a este respecto es el siguiente:

- Para cualquier Máquina Virtual de Instancia Única que utilice Premium SSD o Ultra Disk para todos los Discos de Datos y del Sistema Operativo, le garantizamos que tendrá una Conectividad de Máquina Virtual de al menos el 99,9 %.
- Para cualquier Máquina Virtual de Instancia Única que utilice Standard SSD Managed Disks para los Discos de Datos y del Sistema Operativo, le garantizamos que tendrá una Conectividad de Máquina Virtual de al menos el 99,5 %.
- Para cualquier Máquina Virtual de Instancia Única que utilice Standard HDD Managed Disks para los Discos de Datos y del Sistema Operativo, le garantizamos que tendrá una Conectividad de Máquina Virtual de al menos el 95 %.

## **SLA para Virtual Machines de dos o más instancias**

Tenemos 2 distintos SLAs para cuando creamos máquinas virtuales con 2 instancias. ¿Qué significa esto? Supongamos que tenemos la misma aplicación web de antes, y dicha aplicación web la instalamos en 2 servidores. Cada servidor tendrá una copia exacta del sitio web, y con un buen balanceador por delante obtendremos el siguiente resultado: el rol “Web Server” tiene “2 instancias” (es decir, 2 máquinas virtuales). EEn dicho caso ya no tenemos un único punto de falla, dado que si un equipo falla, el otro seguirá activo. El SLA a este respecto es el siguiente:

- Para todas las Máquinas Virtuales que tengan instaladas dos o más instancias en dos o más Zonas de Disponibilidad de la misma región de Azure, le garantizamos que tendrá Conectividad de Máquina Virtual como mínimo en una instancia al menos el 99,99 % del tiempo.
- Para todas las Máquinas Virtuales que tengan instaladas dos o más instancias en el mismo Conjunto de Disponibilidad o en el mismo Grupo de Dedicated Host, le garantizamos que tendrá Conectividad de Máquina Virtual como mínimo en una instancia al menos el 99,95 % del tiempo.
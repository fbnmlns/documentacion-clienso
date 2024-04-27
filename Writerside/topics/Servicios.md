# Servicios de Infraestructura

## Autenticación centralizada (Active Directory)

Active Directory (AD) es un servicio de directorio diseñado para entornos Windows Server que permite gestionar y
organizar recursos de red, tales como archivos, usuarios, grupos y dispositivos. Funciona como una base de datos
distribuida y jerárquica que almacena información de infraestructura para facilitar la localización, protección y
administración de dichos recursos.

Desarrollado por Microsoft, Active Directory se basa en el sistema operativo Windows Server y utiliza el protocolo LDAP
para gestionar objetos en red. Su función principal es proporcionar autenticación y autorización a gran escala, siendo
conocido principalmente por sus servicios de dominio (Domain Services). Antes de su introducción con Windows 2000, el
modelo de autenticación y autorización de Microsoft requería dividir las redes en dominios y vincularlos mediante
sistemas de confianza complejos. Active Directory simplificó este proceso al ofrecer una solución integrada para
entornos más grandes y complejos.

### Estructura de Active Directory

#### Bosque

Un bosque en Active Directory es el nivel más alto de la jerarquía de organización dentro de un entorno de red. Actúa
como un límite de seguridad que permite una segregación controlada de la autoridad dentro de la organización. Esto
significa que se pueden delegar derechos y permisos de acceso a diferentes administradores, restringiéndolos a
subconjuntos específicos de recursos. Es posible tener un único bosque en toda la red, y la información del bosque se
almacena en todos los controladores de dominio de los dominios que forman parte de él.

#### Árbol

Un árbol en Active Directory es una estructura que agrupa varios dominios. Todos los dominios dentro de un árbol
comparten el mismo espacio de nombres raíz, lo que significa que comparten un nombre de dominio común. Sin embargo, es
importante destacar que los árboles no representan límites de seguridad o replicación en Active Directory. En otras
palabras, la configuración de seguridad y la replicación de datos no están restringidas por la estructura de árbol en sí
misma. Estas características se gestionan a nivel de dominio y bosque en Active Directory.

#### Dominios

Cada bosque en Active Directory tiene un dominio raíz y puede tener dominios adicionales para crear particiones dentro
del bosque. Los dominios se utilizan para dividir el directorio en partes más pequeñas, lo que ayuda a controlar la
replicación de datos. Cada dominio limita la replicación de Active Directory solo a los controladores de dominio dentro
de ese dominio, lo que puede ayudar a ahorrar ancho de banda y mitigar riesgos de seguridad al evitar la replicación
entre ubicaciones separadas, como en el ejemplo de dos oficinas diferentes.

Cada controlador de dominio contiene una copia completa y actualizada de la base de datos de Active Directory de su
dominio correspondiente, asegurando una replicación constante de la información.

Aunque los dominios eran una característica clave en el modelo anterior de Windows-NT y todavía proporcionan una capa de
seguridad, se recomienda complementar el control de replicación utilizando unidades organizativas (OU) para agrupar y
limitar los permisos de seguridad de manera más granular.

#### Unidades Organizativas (OU)

Una Unidad Organizativa (OU) sirve para organizar la autoridad sobre ciertos recursos dentro de un ámbito. Su función
principal es establecer un límite de seguridad para privilegios y autorizaciones específicas, pero no tiene impacto en
la replicación de objetos en el Directorio Activo (AD).

Las OUs se emplean para delegar el control dentro de diferentes funciones o áreas de una organización. Su uso adecuado
permite implementar y restringir la seguridad y los roles entre distintos grupos, mientras que los dominios se utilizan
para gestionar la replicación de AD.

> Las Unidades Organizativas son de gran utilidad al aplicar políticas de grupo.
>
{style="note"}

## DNS

El Sistema de Nombres de Dominio (DNS) es una parte esencial de las redes que se utiliza para traducir los nombres de
dominio legibles para los humanos en direcciones IP que las computadoras pueden entender. En entornos como Windows
Server 2019, DNS se implementa como un rol de servidor, que puede instalarse mediante herramientas gráficas como el
Administrador del Servidor o a través de comandos en PowerShell.

Cuando se configura un nuevo entorno de Active Directory, DNS se instala automáticamente y se integra con Active
Directory para proporcionar servicios de resolución de nombres dentro del dominio. Active Directory Domain Services (AD
DS) utiliza DNS para ayudar en la localización y comunicación entre los controladores de dominio. Esto significa que
cuando los equipos necesitan realizar operaciones en Active Directory, como autenticación o búsqueda de recursos,
utilizan DNS para encontrar los controladores de dominio relevantes. Del mismo modo, los controladores de dominio
utilizan DNS para identificar y comunicarse entre sí dentro de la red.
El servicio de cliente DNS está presente en todas las versiones de Windows, tanto en sistemas cliente como en
servidores, y se activa por defecto durante la instalación del sistema operativo. Cuando configuramos una conexión de
red TCP/IP y asignamos la dirección IP de un servidor DNS, el cliente DNS utiliza esta información para buscar
controladores de dominio y convertir nombres de equipo en direcciones IP.

Por ejemplo, al iniciar sesión en un dominio de Active Directory, el cliente DNS consulta al servidor DNS para localizar
un controlador de dominio. Una vez que el servidor DNS responde proporcionando la dirección IP del controlador de
dominio, el cliente se comunica con él para iniciar el proceso de autenticación.

Tanto los servicios de servidor DNS como de cliente DNS en Windows Server 2019 utilizan el protocolo DNS, que es parte
integral del conjunto de protocolos TCP/IP. DNS se sitúa en la capa de aplicación del modelo de referencia TCP/IP.

![DNS illustration](dns_in_tcpip.jpg){ border-effect="line" thumbnail="true" width="350"}

## DHCP

El Protocolo de Configuración Dinámica de Host (DHCP) es un sistema cliente-servidor que asigna automáticamente
direcciones IP y otros detalles de configuración, como la máscara de subred y la puerta de enlace predeterminada, a
dispositivos en una red. Se basa en los estándares definidos por el Grupo de Trabajo de Ingeniería de Internet (IETF),
específicamente en RFC 2131 y RFC 2132, y comparte similitudes con el protocolo de arranque (BOOTP). DHCP permite que
los dispositivos obtengan la configuración necesaria para TCP/IP desde un servidor DHCP.

Windows Server 2019 incluye una función de servidor DHCP, que es opcional y puede ser implementada en la red para
asignar direcciones IP y otros parámetros a los clientes DHCP. Todos los sistemas operativos cliente de Windows vienen
con un cliente DHCP incorporado, que está habilitado por defecto y forma parte de la implementación de TCP/IP.

### Ventajas de utilizar DHCP

DHCP ofrece varias ventajas:

- **Configuración fiable de direcciones IP**: Evita errores de configuración debido a la asignación manual de
  direcciones IP, como errores de escritura o conflictos de direcciones al asignar la misma dirección a varios
  dispositivos.
- **Administración de red simplificada**: DHCP ofrece características que reducen la carga de administración de la red,
  como:
    - **Configuración centralizada y automatizada de TCP/IP**: Permite configurar la red desde un único lugar de forma
      automatizada.
    - **Asignación de un rango completo de configuraciones TCP/IP adicionalmente**: Se pueden asignar diversas
      configuraciones mediante opciones DHCP.
    - **Control efectivo de cambios de dirección IP**: Especialmente útil para dispositivos móviles que cambian de
      ubicación en una red inalámbrica.
    - **Reenvío de mensajes DHCP a través de un agente de retransmisión**: Elimina la necesidad de tener un servidor
      DHCP en cada subred al reenviar los mensajes iniciales DHCP a través de un agente de retransmisión DHCP.

### Configuración del DHCP Desde PowerShell

Para el proyecto, DHCP ha sido configurado desde PowerShell de la siguiente manera:

<procedure title="Instalación del servidor DHCP">
    <step>Ejecutar PowerShell como administrador y correr el siguiente comándo: </step>
    <code-block lang="shell">
      Install-WindowsFeature DHCP -IncludeManagementTools
    </code-block>
</procedure>

<procedure title="Configuración del servidor DHCP">
  <step>Importar el módulo</step>
    <code-block lang="shell">
      Import-Module DHCPServer
    </code-block>
  <step>Declarar variables (para facilitar la asignación de redes)</step>
    <code-block lang="shell">
      $ScopeName = "Class 1"
    </code-block>
    <code-block lang="shell">
      $StartRange = "192.168.1.1"
    </code-block>
    <code-block lang="shell">
      $EndRange = "192.168.1.254"
    </code-block>
    <code-block lang="shell">
      $SubnetMask = "192.168.1.254"
    </code-block>
    <code-block lang="shell">
     Add-DhcpServerv4Scope -Name $ScopeName -StartRange $StartRange -EndRange $EndRange
    </code-block>
</procedure>

<procedure title="Exclusión de redes como buena práctica">
    <code-block lang="shell">
      Add-DhcpServerv4Scope -StartRange 192.168.1.120 -EndRange 192.168.1.120 -ScopeId 192.168.1.0
    </code-block>
    <code-block lang="shell">
      Add-DhcpServerv4Scope -StartRange 192.168.1.10 -EndRange 192.168.1.20 -ScopeId 192.168.1.0
    </code-block>
    <code-block lang="shell">
      Add-DhcpServerv4Scope -StartRange 192.168.1.245 -EndRange 192.168.1.250 -ScopeId 192.168.1.0
    </code-block>
</procedure>

## Carpetas compartidas desde el servidor

Un sistema de archivos proporciona diversas funciones para organizar y recuperar archivos en dispositivos de
almacenamiento. Permite estructurar los archivos en una jerarquía y controla su formato y nombres. Los sistemas de
archivos son compatibles con una amplia gama de dispositivos de almacenamiento, como discos duros y medios extraíbles.

En el sistema operativo Windows, todos los sistemas de archivos tienen tres componentes principales:

- **Archivos**: Conjuntos de datos relacionados organizados de manera lógica.
- **Directorios**: Colecciones jerárquicas de directorios y archivos.
- **Volúmenes**: Agrupaciones de directorios y archivos.

### Servidor de archivos

Un servidor de archivos es una computadora encargada del almacenamiento y gestión de archivos de datos para que otras
computadoras en la misma red puedan acceder a los archivos. Permite a los usuarios compartir información a través de una
red sin necesidad de transferir físicamente los archivos.

La función de servidor de archivos de Windows permite a los usuarios compartir archivos mediante almacenamiento
conectado a la red y se integra sin problemas con Active Directory utilizando permisos NTFS. Los archivos se
proporcionan a los usuarios finales a través de recursos compartidos de archivos SMB, que pueden ser asignados como
unidades o accedidos mediante rutas UNC. Las unidades asignadas pueden ser fácilmente configuradas para los usuarios
cuando inician sesión en sus computadoras con Windows que están unidas al dominio, utilizando scripts de inicio de
sesión o reglas de política de grupo.

> Es crucial utilizar NTFS al implementar volúmenes en servidores que alojan múltiples roles y características de
> Windows
> Server, como
> Active Directory Domain Services (AD DS), VSS y DFS (Sistema de Archivos
> Distribuido).
>
{style="note"}

### Grupos de seguridad

En Active Directory, hay dos tipos principales de entidades de seguridad: cuentas de usuario y cuentas de equipo. Estas
cuentas representan personas individuales o equipos dentro de una red. Además, una cuenta de usuario puede ser utilizada
como una cuenta de servicio para ciertas aplicaciones.

Los grupos de seguridad son una herramienta importante en Active Directory que permite agrupar cuentas de usuario,
cuentas de equipo y otros grupos en conjuntos administrables. Esto facilita la gestión de permisos y acceso, ya que las
políticas de seguridad pueden aplicarse a todo el grupo en lugar de individualmente a cada cuenta.

> Los grupos de seguridad son utilizados para asignar permisos a los recursos de la empresa.
>
{style="note"}

## Administrador de recursos del servidor de archivos (File Server Resource Manager)

El Administrador de Recursos del Servidor de Archivos (FSRM) es una herramienta de Windows Server que permite a los
administradores organizar y gestionar eficientemente los archivos almacenados en servidores de archivos. Con FSRM, se
pueden automatizar tareas de clasificación de archivos, aplicar acciones específicas en función de estas
clasificaciones, establecer límites de almacenamiento en carpetas y generar informes detallados sobre el uso del espacio
en disco. Esta herramienta proporciona un control preciso sobre los recursos de almacenamiento, lo que ayuda a mantener
el orden y la eficiencia en el entorno de red.

### Características

- **Administración de cuotas**: Es establecer límites de espacio para volúmenes o carpetas. Estos límites pueden
  aplicarse
  automáticamente a nuevas carpetas creadas en esos volúmenes, y también puedes definir plantillas para aplicar cuotas a
  nuevos volúmenes o carpetas.
- **Infraestructura de clasificación de archivos**: Se trata de obtener información sobre los datos mediante la
  clasificación
  automática o manual de archivos. Esto permite administrar los datos de manera más eficiente, aplicando directivas como
  control de acceso, cifrado o expiración de archivos, según su clasificación.
- **Tareas de administración de archivos**: Son acciones o directivas que se aplican a los archivos basadas en
  condiciones
  como ubicación, propiedades de clasificación, fecha de creación o modificación, o último acceso. Las acciones pueden
  incluir expirar archivos, cifrarlos o ejecutar comandos personalizados.
  Administración de filtrado de archivos: Consiste en controlar los tipos de archivos que los usuarios pueden almacenar
  en
  un servidor de archivos, limitando extensiones específicas. Por ejemplo, se puede configurar para no permitir archivos
  con extensión MP3 en carpetas compartidas.
- **Informes de almacenamiento**: Son herramientas para identificar tendencias de uso de disco y cómo se clasifican los
  datos.
  También permiten monitorear grupos de usuarios para detectar intentos de guardar archivos no autorizados.

## Políticas de grupo

Las Directivas de Grupo se utilizan para regular las configuraciones de usuarios y equipos dentro de los dominios de
Active Directory (AD) de Windows. Es un enfoque basado en políticas que puede aplicarse a toda la organización o de
manera selectiva a ciertos departamentos o grupos dentro de las organizaciones. Las Directivas de Grupo son
implementadas mediante Objetos de Directiva de Grupo (GPO, por sus siglas en inglés).

### Objetos de políticas de grupo

Los GPO comprenden las configuraciones de usuario y equipo que se aplicarán a dominios o unidades organizativas (OU).
Los GPO deben estar vinculados a una unidad de AD (dominio o OU) para ser aplicables. Tanto las políticas de
configuración de usuario como de equipo incluyen Configuraciones de Software, Configuraciones de Windows y Plantillas
Administrativas. Las Configuraciones de Windows contienen políticas de seguridad importantes como contraseñas y
políticas de bloqueo de cuentas, restricciones de software y configuraciones de registro. Las Plantillas Administrativas
se utilizan para regular el acceso al Panel de Control, configuraciones del sistema y recursos de red.

- **Configuración de equipo**: Estas políticas se aplican al equipo local y no cambian por usuario.
- **Configuración de usuario**: Estas políticas se le aplican al usuario que ha iniciado sesión y controlan su sesión.

• Web server utilizando http y https
• Certificate Authority (CA) para certificado de la página web
• Folder redirection del directorio “Mis Documentos” del perfil del usuario en las estaciones.

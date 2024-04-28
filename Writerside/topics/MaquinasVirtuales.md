# Máquinas Virtuales

Las máquinas virtuales permiten a una empresa ejecutar un sistema operativo que se comporta como una computadora
completamente separada dentro de una ventana de aplicación en un escritorio. Se pueden implementar máquinas virtuales
para adaptarse a diferentes necesidades de potencia de procesamiento, ejecutar software que requiera un sistema
operativo diferente o probar aplicaciones en un entorno seguro y aislado.

A lo largo de la historia, las máquinas virtuales se han utilizado para la virtualización de servidores, lo que permite
a los
equipos de TI consolidar sus recursos informáticos y mejorar la eficiencia. Además, las máquinas virtuales pueden
realizar tareas específicas consideradas demasiado riesgosas para llevar a cabo en un entorno de host, como acceder a
datos infectados por virus o probar sistemas operativos. Dado que la máquina virtual está separada del resto del
sistema, el software dentro de la máquina virtual no puede interferir con la computadora host.

## Windows Server (Servidor Windows)

Windows Server es un sistema operativo poderoso y flexible ampliamente utilizado por las empresas para alojar
aplicaciones, proporcionar acceso seguro a datos y gestionar la infraestructura de red. Con sus avanzadas capacidades de
virtualización, escalabilidad, características de seguridad e integración con otros productos de Microsoft, ofrece una
variedad de beneficios que pueden ayudar a las empresas a modernizarse y mantenerse flexibles ante las cambiantes
necesidades empresariales.

## Windows Client (Cliente Windows)

Un cliente de Windows es esencial para gestionar y acceder a los recursos compartidos, aplicaciones y servicios alojados
en el servidor, así como el entorno empresarial de ClienSO, donde se utilizan dominios para centralizar la
administración de
usuarios, permisos y políticas de seguridad. Con dicho cliente adecuadamente configurado, los usuarios pueden
autenticarse en el dominio, acceder a recursos compartidos de red, y utilizar otras funcionalidades críticas para la
productividad y la colaboración en el entorno empresarial.

> Para este proyecto se han utilizado los sistemas operativos Windows Server 2019 y Windows 10.
>
{style="note"}

## Instalación

<procedure title="Descargar la imagen de cada sistema operativo">
  <p>Las imágenes pueden ser encontradas ingresando a los siguientes links:</p>
  <list>
    <li>
      <a href="https://www.microsoft.com/es-mx/evalcenter/download-windows-server-2019">Windows Server 10</a>
    </li>
    <li>
      <a href="https://www.microsoft.com/es-es/software-download/windows10">Windows 10</a>
    </li>
  </list>
</procedure>

Una vez con las imagenes descargadas, ingresar a VirtualBox y darle click al
botón ![New virtual machine button](new_virtualmachine_button.png){width="32"} para crear una nueva máquina virtual. Una
vez ahí, seleccionar el archivo .ISO para definir el sistema operativo de la máquina que se desea crear, como se muestra
en la imagen:

![VirtualBox Wizard](virtualmachine_creation.png){ border-effect="line" thumbnail="true" width="550" }

> Se recomienda utilizar la edición Pro dado a que solo esta edición permite las conexiones a dominios.
>
{style="note"}

En las siguientes ventanas, queda a elección del usuario los párametros de hardware que desea tener para su máquina
virtual.

> Tomar en cuenta la capacidad del equipo donde se estarán alojando las máquinas virtuales.
>
{style="warning"}

Estos son los parámetros seleccionados para el cliente del proyecto. La máquina fue creada con 50 GB de memoria, lo
cual permite una correcta funcionalidad.

![Client virtual machine overview](virtualmachine_overview.png){ border-effect="line" thumbnail="true" width="450" }
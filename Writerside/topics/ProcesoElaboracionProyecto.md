# Proceso de Elaboración del Proyecto

## Requerimientos

La empresa ha solicitado que el producto cumpla con los siguientes requerimientos:

1. Los usuarios deberán ser facilitados con un acceso directo a las carpetas compartidas en el escritorio.
2. Los usuarios no deberán poder copiar archivos de tipo .MP3 y .AVI a las carpetas de la empresa.
3. Los usuarios deberán tener el mismo fondo de pantalla que la empresa ha definido.
4. Los usuarios que no pertenecen al departamento de TI deberán tener restringido el acceso al panel de control.
5. Los usuarios deberán tener acceso al sitio web de la empresa.
6. La página inicial de Internet Explorer deberá ser el sitio web de la empresa.
7. Los usuarios deberán tener deshabilitado la ejecución de los ejecutables notepad.exe y regedit.exe.
8. Los usuarios deberán tener mapeada la unidad P: para uso personal.
9. Los usuarios deberán acceder a su carpeta personal mediante una ruta DFS.
10. El usuario administrador local deberá ser nombrado como “usrmda”.
11. El usuario invitado local deberá ser nombrado como “usrtmp”.
12. El usuario administrador no deberá tener la necesidad de intervenir en el cliente para implementar las
    funcionalidades.
13. El contenido dentro de la carpeta “Documentos” de cada usuario deberá dirigirse a una carpeta localizada en el
    servidor.

## Desglose del Trabajo

<procedure title="Primera parte" collapsible="true">
  <procedure title="Arquitectura">
    <p>Creación del ambiente del proyecto</p>
    <step>Windows Server 2019</step>
    <step>Windows 10</step>
  </procedure>
  <procedure title="Configuraciones en el servidor">
    <step>Definir direccionamiento</step>
    <step>AD DS, DHCP y DNS</step>
    <step>Convertir el servidor en Domain Controller (DNS)</step>
    <step>Configuración del DHCP</step>
    <step>Unir el cliente al dominio</step>
  </procedure>
  <procedure title="Pruebas de funcionalidad">
    <step>Pruebas de ping (comunicación cliente - servidor)</step>
    <step>Ingresar con usuario administrador</step>
    <step>Crear usuarios adicionales e ingresar desde el cliente</step>
    <step>Crear carpetas nuevas y accederlas desde el cliente</step>
  </procedure>
</procedure>

<procedure title="Segunda parte" collapsible="true">
  <procedure title="Arquitectura">
    <p>Creación del ambiente del proyecto</p>
    <step>Windows Server 2019</step>
    <step>Windows 10</step>
  </procedure>
  <procedure title="Configuraciones en el servidor">
    <step>Servicios FSRM, IIS y DFS</step>
    <step>Grupos y unidades organizacionales</step>
    <step>Políticas de grupo</step>
    <step>Unir el cliente al dominio</step>
  </procedure>
  <procedure title="Creación del sitio web">
    <step>Tres páginas html navegables</step>
    <step>Asignación de un CA</step>
  </procedure>
  <procedure title="Pruebas de funcionalidad">
    <step>Sitio web es seguro</step>
    <step>Sitio web es funcional</step>
    <step>Carpetas compartidas con permisos y cuotas correctas</step>
    <step>Políticas de grupo funcionan debidamente y el administrador no interviene en el cliente</step>
  </procedure>
  <procedure title="Documentación">
    <step>Guía para el equipo de TI</step>
    <step>Bitácora deja de ser un borrador y pasa a ser un documento oficial</step>
    <step>Presentación post-mortem en formato PechaKucha</step>
  </procedure>
</procedure>

## Cronograma

<table width="100%">
  <tr>
    <th>Semana</th>
    <th>Tarea</th>
  </tr>
  <tr>
    <td>Semana 3</td>
    <td>Entrega del enunciado del proyecto</td>
  </tr>
  <tr>
    <td>Semana 6</td>
    <td>
      <list type="bullet">
        <li>Asignación de tareas y responsabilidades para la 1era parte del proyecto</li>
        <li>Instalación de las máquinas</li>
        <li>Definición del rango de direcciones IP a utilizar</li>
        <li>Instalación de los servicios principales: AC DS, DHCP y DNS</li>
    </list>
    </td>
  </tr>
  <tr>
    <td>Semana 7</td>
    <td>Unión del cliente al dominio</td>
  </tr>
  <tr>
    <td>Semana 8</td>
    <td>Entrega del 1er avance del proyecto</td>
  </tr>
  <tr>
    <td>Semana 9</td>
    <td>Asignación de tareas y responsabilidades para la 2da parte del proyecto</td>
  </tr>
  <tr>
    <td>Semana 11</td>
    <td>Creación de grupos y unidades organizacionales</td>
  </tr>
  <tr>
    <td>Semana 13</td>
    <td>
      <list type="bullet">
        <li>Inicio de la creación de políticas de grupo</li>
        <li>Instalación del servicio FSRM y configuración de las cuotas de almacenamiento</li>
        <li>Creación del sitio web</li>
        <li>Instalación del IIS y creación del sitio web</li>
    </list>
</td>
  </tr>
  <tr>
    <td>Semana 14</td>
    <td>
      <list type="bullet">
        <li>Finalización de la creación de políticas de grupo</li>
        <li>Creación del CA para el sitio web</li>
        <li>Instalación del servicio DFS</li>
        <li>Realización de pruebas finales</li>
    </list>
</td>
  </tr>
  <tr>
    <td>Semana 15</td>
    <td>Entrega final del proyecto</td>
  </tr>
</table>

## Bitácora

Se puede acceder a la bitácora que documenta todo el trabajo realizado para la elaboración del proyecto a través del
siguiente link: [Bitácora del Grupo 1](https://drive.google.com/file/d/1emXU9Fq53S2bZ9O5C2FTT1rhXxcTINZ2/view?usp=drive_link)

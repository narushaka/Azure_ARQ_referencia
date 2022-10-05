<!-- los # o el h1 definen el tamano de la letra -->

<body bgcolor="#141D2B">

<div>
<p style = 'text-align:center;'>
<img src="https://www.svgrepo.com/show/353464/azure.svg" alt="JuveYell" width="300px">
</p>
</div>

<p><br>

<h1> <span style="color:#0089D6"> Servicios de archivos híbridos
  </span> 


<!-- italic -->


<!-- genero espaciado copn el comando <p><br> -->


<p><br>



<!-- el ** define que le texto este en NEGRILLA O STRONG -->

<!-- el ~~ define que le texto este TACHADO -->

<h2> <span style="color:#0089D6"> Contexto   </span> </h1>

<p><br>

<p style="color:#A4B1CD;">Esta arquitectura de referencia ilustra cómo usar Azure File Sync y Azure Files para ampliar las funcionalidades de hospedaje de servicios de archivos en recursos compartidos de archivos locales y en la nube.</p>


<p><br>
<p><br>

<img src="https://learn.microsoft.com/en-us/azure/architecture/hybrid/images/hybrid-file-services.png" width="1000px">

<p><br>
<p><br>


<h1> <span style="color:#0089D6">  Flujo de trabajo </span> </h1>

<p><br>
<p><br>

<p style="color:#A4B1CD;"> La arquitectura consta de los siguientes componentes:</p>

<p style="color:#A4B1CD;">- Cuenta de almacenamiento. Una cuenta de almacenamiento de Azure que se usa para hospedar recursos compartidos de archivos de Microsoft Azure.</p>

<p style="color:#A4B1CD;"> - Azure Files. Un recurso compartido de archivos en la nube sin servidor que proporciona el extremo en la nube de una relación de sincronización con Azure File Sync. Se puede acceder a los archivos de un recurso compartido de archivos de Azure directamente con server Message Block (SMB) o el protocolo FileREST. </p>

<p style="color:#A4B1CD;"> - Sincronizar grupos. Agrupaciones lógicas de recursos compartidos de archivos de Azure y servidores que ejecutan Windows Server. Los grupos de sincronización se implementan en el Servicio de sincronización de almacenamiento, que registra los servidores para su uso con Azure File Sync y contiene las relaciones de grupo de sincronización. </p>

<p style="color:#A4B1CD;">- Agente de Azure File Sync. Esto se instala en máquinas con Windows Server para habilitar y configurar la sincronización con puntos de conexión en la nube.  </p>

<p style="color:#A4B1CD;"> - Servidores Windows. Máquinas Windows Server locales o basadas en la nube que hospedan un recurso compartido de archivos que se sincroniza con un recurso compartido de archivos de Azure. </p>

<p style="color:#A4B1CD;">- Azure Active Directory. El inquilino de Azure Active Directory (Azure AD) que se usa para la sincronización de identidades en entornos locales y de Azure.</p>
<p><br>
<p><br>
<h1> <span style="color:#0089D6">  Detalles del escenario  </span> </h1>


<p><br>




<p style="color:#A4B1CD;"> Los usos típicos de esta arquitectura incluyen: </p>

<p style="color:#A4B1CD;">1) Hospedar recursos compartidos de archivos a los que se debe acceder desde entornos locales y en la nube.</p>

<p style="color:#A4B1CD;"> 2) Sincronización de datos entre varios almacenes de datos locales con un único origen basado en la nube.</p> 
<p><br>
<p><br>

<h1> <span style="color:#0089D6">  Uso e implementación de Azure Files </h1>


<p><br>



<p style="color:#A4B1CD;"> Los archivos se almacenan en la nube en recursos compartidos de archivos de Azure. Puede usar recursos compartidos de archivos de Azure de dos maneras: montando directamente estos recursos compartidos de archivos de Azure (SMB) sin servidor o almacenando en caché recursos compartidos de archivos de Azure localmente mediante Azure File Sync. La opción de implementación que elija cambia lo que debe tener en cuenta al planear la implementación: </p> 

<p style="color:#A4B1CD;">  Montaje directo de un recurso compartido de archivos de Azure. Dado que Azure Files proporciona acceso A SMB, puede montar recursos compartidos de archivos de Azure localmente o en la nube con el cliente SMB estándar disponible en los sistemas operativos Windows, macOS y Linux. Los recursos compartidos de archivos de Azure no tienen servidor, por lo que la implementación para escenarios de producción no requiere la administración de un servidor de archivos o un dispositivo de almacenamiento conectado a la red (NAS). Esto significa que no tiene que aplicar parches de software o intercambiar discos físicos.</p> 


<p><br>
<p><br>



<h1> <span style="color:#0089D6"> Componentes  </span> </h1> 

<p><br>

<h2> <span style="color:#0089D6"> Azure AD TENANT </span> </h2>

<p><br>

<img src="https://aidanfinn.com/wp-content/uploads/2015/06/azure-active-directory1.png" alt="JuveYell" width="200px">
<p><br>



<p><br>

<p style="color:#A4B1CD;"> Un Tenant de Azure es una instancia dedicada y confiable de Azure AD que se crea automáticamente cuando nuestra organización se suscribe a un servicio en la nube de Azure. Este Tenant representa a la organización y es independiente de otros Tenant.</p>


<p><br>
<p><br>

<h2> <span style="color:#0089D6"> Azure Files share  </span> </h2>

<p><br>
<p><br>

<img src="https://www.ciraltos.com/wp-content/uploads/2020/04/Azure-Storage-Files-300x300.png" alt="JuveYell" width="200px">

<p style="color:#A4B1CD;">Es la aplicacion  más rápida de comenzar a desarrollar e implementar aplicaciones nativas de la nube, con canalizaciones y barreras de protección integradas de código a nube. Obtenga administración y gobernanza unificadas para clústeres de Kubernetes locales, perimetrales y multinube. Interopere con los servicios de seguridad, identidad, administración de costos y migración de Azure.</p>

<p><br>
<p><br>

<h2> <span style="color:#0089D6"> Azure AD CONNECT  </span> </h2>

<p><br>
<p><br>



<p style="color:#A4B1CD;"> Azure AD Connect es una herramienta para conectar la infraestructura de identidad local a Microsoft Azure AD. El asistente implementa y configura los requisitos previos y los componentes necesarios para la conexión, incluida la sincronización y el inicio de sesión. [1] Azure AD Connect abarca la funcionalidad que se publicó anteriormente como Dirsync y AAD Sync. Estas herramientas ya no se publican individualmente y todas las mejoras futuras se incluirán en las actualizaciones de Azure AD Connect</p>



<p><br>

<h2> <span style="color:#0089D6"> Azure File server agent </span> </h2>

<p><br>





<p style="color:#A4B1CD;"> es el agente  para centralizar los recursos compartidos de archivos de su organización en Azure Files sin renunciar a la flexibilidad, el rendimiento y la compatibilidad de un servidor de archivos local. Azure File Sync transforma Windows Server en una caché rápida de los recursos compartidos de archivos de Azure. Puede usar cualquier protocolo disponible en Windows Server para acceder a sus datos localmente, como SMB, NFS y FTPS. Puede tener todas las cachés que necesite en todo el mundo.</p>

<p style="color:#A4B1CD;"> Almacenes para guardar y administrar claves criptográficas, secretos, certificados y claves de cuentas de almacenamiento.
Grupo de HSM administrado para almacenar y administrar claves criptográficas respaldadas por HSM</p>
<p><br>
<p><br>
<p><br>


<p style="color:#A4B1CD;"> Para mas informacion y detalles del escenario a implementar.</p>

https://learn.microsoft.com/en-us/azure/architecture/hybrid/hybrid-file-services

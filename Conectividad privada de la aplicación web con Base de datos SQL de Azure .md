<!-- los # o el h1 definen el tamano de la letra -->

<body bgcolor="#141D2B">

<div>
<p style = 'text-align:center;'>
<img src="https://www.svgrepo.com/show/353464/azure.svg" alt="JuveYell" width="300px">
</p>
</div>



<h1> <span style="color:#0089D6"> Conectividad privada de la aplicación web con Base de datos SQL de Azure </span> 


<!-- italic -->


<!-- genero espaciado copn el comando <p><br> -->


<p><br>




<!-- el ** define que le texto este en NEGRILLA O STRONG -->

<!-- el ~~ define que le texto este TACHADO -->

<h2> <span style="color:#0089D6"> Contexto</span> </h1>

<p><br>

<p style="color:#A4B1CD;">En este escenario de ejemplo se describe cómo conectar de forma segura una aplicación web a una base de datos back-end a través de una conexión totalmente privada. La comunicación garantiza desde la aplicación web en el Servicio de aplicaciones de Azure y Base de datos SQL de Azure solo atraviesa una red virtual.</p>


<p><br>
<p><br>

<img src="https://docs.microsoft.com/en-us/azure/architecture/example-scenario/private-web-app/media/private-webapp-appsvc-private-sql-v6.png" alt="JuveYell" width="1000px">

<p><br>
<p><br>


<h2> <span style="color:#0089D6"> Analisis de la arquitectura</span> </h1>

<p><br>
<p><br>

<p style="color:#A4B1CD;">
1) La aplicación web recibe una solicitud HTTP de Internet que requiere una llamada a la API a Base de datos SQL de Azure.<br><br>
2) Las aplicaciones web hospedadas en el Servicio de aplicaciones solo pueden llegar a los extremos hospedados en Internet de forma predeterminada. Pero la configuración de la integración de red virtual regional proporciona a la aplicación web acceso saliente a los recursos de la red virtual que no son un punto final hospedado en Internet. La integración de red regional monta una interfaz virtual en AppSvcSubnet. Aplicamos la configuración *Route All a la integración de la red regional. Todo el tráfico saliente de la aplicación web pasa por la red virtual.<br><br>
3) La aplicación web se conecta a la red virtual a través de una interfaz virtual montada en appSvcSubnet de la red virtual.<br><br>
4) Azure Private Link configura un punto de conexión privado para Base de datos SQL de Azure en PrivateLinkSubnet de la red virtual.<br><br>
5) La aplicación web envía una consulta DNS saliente para la dirección IP de Base de datos SQL de Azure a través de la interfaz virtual de AppSvcSubnet. El CNAME del DNS de la base de datos dirige la consulta DNS a la zona DNS privada. La zona DNS privada devuelve la dirección IP privada del punto de conexión privado de Base de datos SQL de Azure.<br><br>
6) La aplicación web se conecta a Base de datos SQL a través del extremo privado de PrivateLinkSubnet.<br><br>
7) El firewall de la base de datos solo permite que el tráfico procedente de PrivateLinkSubnet se conecte. La base de datos es inaccesible desde la Internet pública. </p> </p>


<p><br>
<h2> <span style="color:#0089D6"> Componentes arquitectonicos</span> </h1>
<p><br>

<h3> <span style="color:#0089D6">Virtual machine de Azure</span> </h3>
<p><br>


<img src="https://ms-azuretools.gallerycdn.vsassets.io/extensions/ms-azuretools/vscode-azureappservice/0.20.0/1604973785944/Microsoft.VisualStudio.Services.Icons.Default" alt="JuveYell" width="120px">
<p><br>

<p style="color:#A4B1CD;">Hospeda aplicaciones web, lo que permite el escalado automático y la alta disponibilidad sin tener que administrar la infraestructura.</p>

<p><br>
<h3> <span style="color:#0089D6">Azure database SQL </span> </h3>

<p><br>
<img src="https://www.freelogovectors.net/wp-content/uploads/2022/03/azure_sql_database_logo_freelogovectors.net_.png" alt="JuveYell" width="120px">
<p><br>



<p style="color:#A4B1CD;"> Es un servicio administrado de base de datos relacional de uso general que admite datos relacionales, datos espaciales, JSON y XML. </p>


<p><br>
<h3> <span style="color:#0089D6">Azure Virtual Network</span> </h3>
<p><br>


<p><br>
<img src="https://symbols.getvecta.com/stencil_28/71_virtual-network.8cd684329b.svg" alt="JuveYell" width="150px">
<p><br>



<p style="color:#A4B1CD;"> es el bloque de creación fundamental para las redes privadas en Azure. Los recursos de Azure, como las máquinas virtuales (VM), pueden comunicarse de forma segura entre sí, con Internet y con las redes locales a través de redes virtuales. 
</p>

<p><br>
<h3> <span style="color:#0089D6">Azure Private Link</span> </h3>
<p><br>


<p><br>
<img src="https://www.starwindsoftware.com/blog/wp-content/uploads/2020/03/resultat-de-recherche-dimages-pour-azure-private.png" alt="JuveYell" width="150px">
<p><br>



<p style="color:#A4B1CD;"> El firewall de la base de datos solo permite que el tráfico procedente de PrivateLinkSubnet se conecte. La base de datos es inaccesible desde la Internet pública.
</p>



<p><br>
<h2> <span style="color:#0089D6"> Posibles casos de uso </span> </h1>
<p><br>


<p style="color:#A4B1CD;">
1) Conectividad privada desde un Servicio de aplicaciones de Azure a servicios de plataforma como servicio (PaaS) de Azure.<br><br>
2) LConectividad privada desde un Servicio de aplicaciones de Azure a servicios PaaS de Azure que no se implementan de forma nativa en redes virtuales de Azure aisladas.<br><br>
3) Conéctese desde el Servicio de aplicaciones de Azure a Almacenamiento de Azure, Azure Cosmos DB, Azure Cognitive Search, Azure Event Grid o cualquier otro servicio que admita un punto de conexión privado de Azure para la conectividad entrante.<br><br>


<p><br>
<h2> <span style="color:#0089D6"> Seguridad</span> </h1>
<p><br>


<p style="color:#A4B1CD;">
La arquitectura crea una conexión saliente segura desde una aplicación web del Servicio de aplicaciones a una dependencia descendente, como una base de datos. También puede proteger la conexión entrante a la aplicación web. El fronting de la aplicación con un servicio como Application Gateway o Azure Front Door mejora la seguridad de entrada de la aplicación web. Para mayor seguridad de entrada, puede integrar Azure Web Application Firewall tanto en Application Gateway como en Azure Front Door.<br><br>


<p><br>
<h2> <span style="color:#0089D6"> Peering global </span> </h1>
<p><br>

<p style="color:#A4B1CD;">Cualquier servicio de cualquier región de Azure que pueda conectarse a través de la red virtual puede llegar al punto de conexión privado de la base de datos. Por ejemplo, el emparejamiento de red virtual en topologías de concentrador y radio habilitaría la conectividad con el extremo privado.<p><br>

<p style="color:#A4B1CD;">Lo mismo ocurre cuando se usa la integración de red virtual regional del Servicio de aplicaciones. La integración de redes virtuales regionales es una solución para la conectividad entre regiones desde el Servicio de aplicaciones a una base de datos u otro punto de conexión privado en otra región de Azure. Puede crear una aplicación web de varias regiones con conectividad privada a una base de datos. Esta arquitectura de varias regiones admite conmutaciones por error parciales cuando la aplicación web o la base de datos conmutan por error a otra región.<p><br>


<p style="color:#A4B1CD;">Los puntos de conexión privados para Base de datos SQL de Azure están disponibles en todas las regiones públicas y gubernamentales. El punto de conexión privado tiene un SLA de disponibilidad del 99,99 %. El SLA debe tenerse en cuenta al calcular el SLA compuesto de toda la solución.<p><br>


https://docs.microsoft.com/en-us/azure/architecture/example-scenario/private-web-app/private-web-app
<!-- los # o el h1 definen el tamano de la letra -->

<body bgcolor="#141D2B">

<div>
<p style = 'text-align:center;'>
<img src="https://www.svgrepo.com/show/353464/azure.svg" alt="JuveYell" width="300px">
</p>
</div>

<p><br>

<h1> <span style="color:#0089D6"> Arquitectura de microservicios en Azure Kubernetes Service  </span> 


<!-- italic -->


<!-- genero espaciado copn el comando <p><br> -->


<p><br>



<!-- el ** define que le texto este en NEGRILLA O STRONG -->

<!-- el ~~ define que le texto este TACHADO -->

<h2> <span style="color:#0089D6"> Contexto  </span> </h1>

<p><br>

<p style="color:#A4B1CD;">Esta arquitectura es para aplicaciones globales orientadas a Internet que utilizan protocolos HTTP(S) y TCP. Cuenta con equilibrio de carga global basado en DNS, dos formas de equilibrio de carga regional y emparejamiento de red virtual global para crear una arquitectura de alta disponibilidad que pueda soportar una interrupción regional.</p>


<p><br>
<p><br>

<img src="https://learn.microsoft.com/en-us/azure/architecture/high-availability/images/high-availability-multi-region-v-8.png" alt="JuveYell" width="1000px">

<p><br>
<p><br>


<h2> <span style="color:#0089D6"> Flujo de trabajo  </span> </h1>

<p><br>
<p><br>



<p style="color:#A4B1CD;">1) Azure Traffic Manager usa el enrutamiento basado en DNS para equilibrar la carga del tráfico entrante en las dos regiones. El Administrador de tráfico resuelve las consultas DNS de la aplicación a las direcciones IP públicas de los extremos de Application Gateway (AppGW). Los puntos de conexión públicos de los AppGW sirven como extremos back-end del Administrador de tráfico. Traffic Manager resuelve las consultas DNS en función de una selección de seis métodos de enrutamiento. El navegador se conecta directamente al punto final. El Administrador de tráfico no ve el tráfico HTTP(S).</p>

<p style="color:#A4B1CD;"> 2) Las application gateways (AppGW) reciben tráfico HTTP(S) del explorador y equilibran la carga de las solicitudes en el grupo back-end de máquinas virtuales (VM) del nivel web. La implementación de los AppGWs en las tres zonas proporciona redundancia de zona para los AppGWs. Los AppGW también distribuyen el tráfico entre las tres zonas del nivel web. Los AppGW incluyen un firewall de aplicaciones web (WAF) que inspecciona el tráfico y protege la aplicación de vulnerabilidades y vulnerabilidades web.</p>

<p style="color:#A4B1CD;"> 3) El nivel web es la primera capa de la aplicación de tres niveles. Hospeda máquinas virtuales en tres zonas de disponibilidad. Las puertas de enlace de aplicaciones distribuyen el tráfico a cada una de las tres zonas de disponibilidad. El nivel web contiene la interfaz de usuario. También analiza las interacciones de los usuarios y pasa el tráfico destinado al nivel de datos al equilibrador de carga interno..</p>

<p style="color:#A4B1CD;">4) Los equilibradores de carga internos distribuyen el tráfico a las máquinas virtuales de nivel empresarial en las tres zonas de disponibilidad. Utilizan una única dirección IP privada para facilitar la configuración. Las direcciones IP privadas de los equilibradores de carga son redundantes de zona. Las direcciones IP persisten en las tres zonas y pueden sobrevivir a cualquier error de una sola zona.</p>

<p style="color:#A4B1CD;">5) Almacenes de datos externos. Los microservicios suelen ser sin estado y escribir estado en almacenes de datos externos, como Azure El nivel de negocio procesa las interacciones del usuario y determina los siguientes pasos. Conecta la web y los niveles de datos. Las máquinas virtuales del nivel empresarial enrutan el tráfico al agente de escucha del grupo de disponibilidad de las bases de datos.

</p>

<p style="color:#A4B1CD;">6) El nivel de datos almacena los datos de la aplicación, normalmente en una base de datos, almacenamiento de objetos o recurso compartido de archivos. La arquitectura tiene SQL Server en máquinas virtuales distribuidas en tres zonas de disponibilidad. Están en un grupo de disponibilidad y usan un nombre de red distribuida (DNN) para enrutar el tráfico al agente de escucha del grupo de disponibilidad para el equilibrio de carga.</p>


<p><br>
<p><br>



<h1> <span style="color:#0089D6"> Componentes  </span> </h1> 

<p><br>

<h2> <span style="color:#0089D6"> Máquinas virtuales de Azure  </span> </h2>

<p><br>

<img src="https://4.bp.blogspot.com/-6kxXPrWRJgg/WQU0DaEYDsI/AAAAAAAAHmE/Je6tStW7R3kxuHDVEA3kImKH80hDm9DUACLcB/s320/vm.png" alt="JuveYell" width="200px">
<p><br>



<p><br>

<p style="color:#A4B1CD;"> Las máquinas virtuales son recursos informáticos escalables y bajo demanda que le brindan la flexibilidad de la virtualización, pero eliminan las demandas de mantenimiento del hardware físico. Las opciones de sistema operativo incluyen Windows y Linux..</p>


<p><br>
<p><br>

<h2> <span style="color:#0089D6"> Azure Kubernetes Service (AKS)  </span> </h2>

<p><br>
<p><br>

<img src="https://symbols.getvecta.com/stencil_27/101_vm-scale-set.cf13d24fc9.svg" alt="JuveYell" width="200px">
<p><br>
<p style="color:#A4B1CD;"> Es el escalado de máquinas virtuales automatizado y con equilibrio de carga que simplifica la administración de las aplicaciones y aumenta la disponibilidad.</p>

<p><br>
<p><br>

<h2> <span style="color:#0089D6"> El Administrador de tráfico  </span> </h2>

<p><br>
<p><br>

<img src="https://symbols.getvecta.com/stencil_27/96_traffic-manager.48c46d4d57.svg" alt="JuveYell" width="200px">


<p><br>
<p><br>



<p style="color:#A4B1CD;">  un trafic manager o un es un equilibrador de carga de tráfico basado en DNS que distribuye el tráfico a los servicios en las regiones globales de Azure al tiempo que proporciona alta disponibilidad y capacidad de respuesta. Para obtener más información, consulte la sección Configuración del Administrador de tráfico.</p>



<p><br>

<h2> <span style="color:#0089D6"> Application gateway </span> </h2>

<p><br>
<p><br>

<img src="https://symbols.getvecta.com/stencil_27/11_application-gateway.5516881001.svg" alt="JuveYell" width="200px">


<p><br>


<p style="color:#A4B1CD;"> es un equilibrador de carga de capa 7. La SKU v2 de Application Gateway admite la redundancia entre zonas. Una sola implementación de Application Gateway puede ejecutar varias instancias de la puerta de enlace. </p>




<p><br>

<h2> <span style="color:#0089D6"> Azure Load Balancer </span> </h2>

<p><br>
<p><br>

<img src="https://symbols.getvecta.com/stencil_27/56_load-balancer-feature.d9e31930a2.svg" alt="JuveYell" width="200px">


<p><br>


<p style="color:#A4B1CD;"> es un equilibrador de carga de capa 4. Un equilibrador de carga con redundancia de zona seguirá distribuyendo el tráfico con un error de zona. </p>



<p><br>

<h2> <span style="color:#0089D6"> Azure DDoS Protection </span> </h2>

<p><br>
<p><br>

<img src="https://azure.microsoft.com/svghandler/ddos-protection/?width=600&height=315" alt="JuveYell" width="200px">


<p><br>


<p style="color:#A4B1CD;"> tiene características mejoradas para proteger contra ataques de denegación de servicio distribuido (DDoS). </p>


<p><br>

<h2> <span style="color:#0089D6">Azure DNS   </span> </h2>


<p><br>
<p><br>


<p style="color:#A4B1CD;"> es un servicio de hospedaje para dominios DNS. Proporciona resolución de nombres mediante la infraestructura de Microsoft Azure. Al hospedar sus dominios en Azure, puede administrar sus registros DNS con las mismas credenciales, API, herramientas y facturación que sus otros servicios de Azure. </p>

<p><br>

<h2> <span style="color:#0089D6">Las zonas DNS privadas    </span> </h2>

<p><br>
<p><br>


<img src="https://azure.microsoft.com/svghandler/dns/?width=600&height=315" alt="JuveYell" width="200px">

<p><br>

<p style="color:#A4B1CD;"> son una característica de DNS de Azure. Las zonas privadas dns de Azure proporcionan resolución de nombres dentro de una red virtual y entre redes virtuales. Los registros contenidos en una zona DNS privada no se pueden resolver desde Internet. La resolución de DNS en una zona DNS privada solo funciona desde redes virtuales vinculadas a ella. </p>



<h2> <span style="color:#0089D6">Azure Virtual Network   </span> </h2>

<p><br>


<p><br>

<p style="color:#A4B1CD;">  es una red privada segura en la nube. Conecta las máquinas virtuales entre sí, con Internet y con las redes locales. </p>

<p><br>
<p><br>

<h2> <span style="color:#0089D6">SQL Server en máquinas virtuales   </span> </h2>


<p><br>

<p style="color:#A4B1CD;">  le permite usar versiones completas de SQL Server en la nube sin tener que administrar ningún hardware local. </p>





<p><br>
<p><br>



<h1> <span style="color:#0089D6"> Detalles de la solución </span> </h1> 





<p style="color:#A4B1CD;">- Configuramos traffic Manager para usar el enrutamiento de rendimiento. Enruta el tráfico al punto final que tiene la latencia más baja para el usuario. Traffic Manager ajusta automáticamente su algoritmo de equilibrio de carga a medida que cambia la latencia del punto final.</p>

<p style="color:#A4B1CD;">- El administrador de tráfico proporciona conmutación por error automática si hay una interrupción regional. Utiliza enrutamiento prioritario y comprobaciones de estado periódicas para determinar dónde enrutar el tráfico.</p>

<p style="color:#A4B1CD;">- La arquitectura utiliza tres zonas para admitir Application Gateway, el equilibrador de carga y cada nivel de aplicación para una alta disponibilidad.</p>

<p style="color:#A4B1CD;">- El Administrador de tráfico proporciona equilibrio de carga basado en DNS, mientras que Application Gateway le ofrece muchas de las mismas funcionalidades que Azure Front Door, pero a nivel regional, como:</p>

<p style="color:#A4B1CD;">Firewall de aplicaciones web (WAF)</p>

<p style="color:#A4B1CD;">Terminación de la seguridad de la capa de transporte (TLS)</p>

<p style="color:#A4B1CD;">Enrutamiento basado en rutas</p>

<p style="color:#A4B1CD;">Afinidad de sesión basada en cookies</p>

<p style="color:#A4B1CD;">- El emparejamiento de red virtual global (red virtual) proporciona replicación de datos de baja latencia y gran ancho de banda entre regiones. Puede transferir datos entre suscripciones de Azure, inquilinos de Azure Active Directory y modelos de implementación con emparejamiento de red virtual global.</p>

<p><br>
<p><br>
<p><br>
<p><br>
<p><br>


https://learn.microsoft.com/en-us/azure/architecture/high-availability/reference-architecture-traffic-manager-application-gateway
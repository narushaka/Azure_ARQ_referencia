<!-- los # o el h1 definen el tamano de la letra -->

<body bgcolor="#141D2B">

<div>
<p style = 'text-align:center;'>
<img src="https://www.svgrepo.com/show/353464/azure.svg" alt="JuveYell" width="300px">
</p>
</div>

<p><br>

<h1> <span style="color:#0089D6">Implementar una red híbrida segura </span> 


<!-- italic -->


<!-- genero espaciado copn el comando <p><br> -->


<p><br>



<!-- el ** define que le texto este en NEGRILLA O STRONG -->

<!-- el ~~ define que le texto este TACHADO -->

<h2> <span style="color:#0089D6"> Contexto </span> </h1>

<p><br>

<p style="color:#A4B1CD;">Esta arquitectura de referencia muestra una red híbrida segura que extiende una red local a Azure. La arquitectura implementa una red perimetral, también denominada DMZ, entre la red local y una red virtual de Azure. Todo el tráfico entrante y saliente pasa a través de Azure Firewall. </p>


<p><br>
<p><br>

<img src="https://learn.microsoft.com/en-us/azure/architecture/reference-architectures/dmz/images/dmz-private.png" width="1000px">

<p><br>
<p><br>



<h2> <span style="color:#0089D6"> Posibles casos de uso </span> </h2>


<p style="color:#A4B1CD;"> Esta arquitectura requiere una conexión al centro de datos local, mediante una puerta de enlace VPN o una conexión ExpressRoute. Los usos típicos de esta arquitectura incluyen:</p>

<p style="color:#A4B1CD;">- Aplicaciones híbridas donde las cargas de trabajo se ejecutan en parte localmente y en parte en Azure.
</p>

<p style="color:#A4B1CD;">- Infraestructura que requiere un control granular sobre el tráfico que entra en una red virtual de Azure desde un centro de datos local.
</p>

<p style="color:#A4B1CD;">- Aplicaciones que deben auditar el tráfico saliente. La auditoría es a menudo un requisito regulatorio de muchos sistemas comerciales y puede ayudar a prevenir la divulgación pública de información privada.
</p>


<h2> <span style="color:#0089D6">Componentes arquitectonicos </span> </h2> 

<p><br>

<p style="color:#A4B1CD;">La arquitectura consta de los siguientes aspectos:</p>


<p style="color:#A4B1CD;">  Red local. Una red de área local privada implementada en una organización. </p>

<p style="color:#A4B1CD;"> - Red virtual de Azure. La red virtual hospeda los componentes de la solución y otros recursos que se ejecutan en Azure. Las rutas de red virtual definen el flujo de tráfico IP dentro de la red virtual de Azure. En el diagrama, hay dos tablas de enrutamiento definidas por el usuario.En la subred de puerta de enlace, el tráfico se enruta a través de la instancia de Azure Firewall.  </p>

<p style="color:#A4B1CD;">- Puerta de enlace. La puerta de enlace proporciona conectividad entre los enrutadores de la red local y la red virtual. La puerta de enlace se coloca en su propia subred. </p>

<p><br>


<p style="color:#A4B1CD;">- Azure Firewall. Azure Firewall es un firewall administrado como servicio. La instancia de Firewall se coloca en su propia subred.

 </p>

<p><br>


<p style="color:#A4B1CD;">-Grupos de seguridad de red. Utilice grupos de seguridad para restringir el tráfico de red dentro de la red virtual. </p>


<p><br>


<p style="color:#A4B1CD;">- Bastión de Azure. Azure Bastion le permite iniciar sesión en máquinas virtuales (VM) en la red virtual a través de SSH o protocolo de escritorio remoto (RDP) sin exponer las máquinas virtuales directamente a Internet. Use Bastion para administrar las máquinas virtuales de la red virtual. </p>
<p><br>


<p><br>

<h2> <span style="color:#0089D6">Posibles casos de uso </span> </h2> 

<p><br>

<p style="color:#A4B1CD;"> Esta arquitectura requiere una conexión al centro de datos local, mediante una puerta de enlace VPN o una conexión ExpressRoute. Los usos típicos de esta arquitectura incluyen: </p>


<p style="color:#A4B1CD;">- Aplicaciones híbridas donde las cargas de trabajo se ejecutan en parte localmente y en parte en Azure. </p>
<p><br>

<p style="color:#A4B1CD;">- Infraestructura que requiere un control granular sobre el tráfico que entra en una red virtual de Azure desde un centro de datos local. </p>

<p><br>

<p style="color:#A4B1CD;">- Aplicaciones que deben auditar el tráfico saliente. La auditoría es a menudo un requisito regulatorio de muchos sistemas comerciales y puede ayudar a prevenir la divulgación pública de información privada. </p>
<p><br>

<p><br>
<h2> <span style="color:#0089D6"> Eficiencia de rendimiento </span> </h2> 


<p><br>

<p style="color:#A4B1CD;">La eficiencia del rendimiento es la capacidad de su carga de trabajo para escalar para satisfacer las demandas que le imponen los usuarios de manera eficiente. Para obtener más información, consulte Información general sobre el pilar de eficiencia del rendimiento.<p>


<p style="color:#A4B1CD;">- Para obtener más información sobre los límites de ancho de banda de VPN Gateway, consulte SKU de puerta de enlace. Para anchos de banda más altos, considere la posibilidad de actualizar a una puerta de enlace expressRoute. ExpressRoute proporciona un ancho de banda de hasta 10 Gbps con una latencia más baja que una conexión VPN.<p>

<p><br>
<h2> <span style="color:#0089D6">Fiabilidad</span> </h2> 

<p style="color:#A4B1CD;">La confiabilidad garantiza que su aplicación pueda cumplir con los compromisos que asume con sus clientes. Para obtener más información, consulte Información general sobre el pilar de confiabilidad.<p>

<p style="color:#A4B1CD;"> Si usa Azure ExpressRoute para proporcionar conectividad entre la red virtual y la red local, configure una puerta de enlace VPN para proporcionar conmutación por error si la conexión ExpressRoute deja de estar disponible. <p>

<p><br>
<h2> <span style="color:#0089D6">Excelencia operativa</span> </h2> 
<p><br>
<p style="color:#A4B1CD;">La excelencia operativa cubre los procesos de operaciones que implementan una aplicación y la mantienen en funcionamiento en producción. Para obtener más información, consulte Información general sobre el pilar de excelencia operativa.<p>

<p style="color:#A4B1CD;"> Si la conectividad de la puerta de enlace desde la red local a Azure está inactiva, aún puede acceder a las máquinas virtuales de la red virtual de Azure a través de Azure Bastion. <p>


<p style="color:#A4B1CD;"> La subred de cada nivel en la arquitectura de referencia está protegida por reglas NSG. Es posible que deba crear una regla para abrir el puerto 3389 para el acceso al protocolo de escritorio remoto (RDP) en máquinas virtuales de Windows o el puerto 22 para el acceso de shell seguro (SSH) en máquinas virtuales Linux. Otras herramientas de administración y monitoreo pueden requerir reglas para abrir puertos adicionales. <p>

<p><br>
<h2> <span style="color:#0089D6">Seguridad</span> </h2> 
<p><br>
<p style="color:#A4B1CD;">La seguridad proporciona garantías contra ataques deliberados y el abuso de sus valiosos datos y sistemas. Para obtener más información, consulte Información general sobre el pilar de seguridad.<p>

<p style="color:#A4B1CD;"> Esta arquitectura de referencia implementa múltiples niveles de seguridad. <p>

https://learn.microsoft.com/en-us/azure/architecture/reference-architectures/dmz/secure-vnet-dmz?tabs=portal
<!-- los # o el h1 definen el tamano de la letra -->

<body bgcolor="#141D2B">

<div>
<p style = 'text-align:center;'>
<img src="https://www.svgrepo.com/show/353464/azure.svg" alt="JuveYell" width="300px">
</p>
</div>

<p><br>

<h1> <span style="color:#0089D6">Conexión de una red local a Azure </span> 


<!-- italic -->


<!-- genero espaciado copn el comando <p><br> -->


<p><br>



<!-- el ** define que le texto este en NEGRILLA O STRONG -->

<!-- el ~~ define que le texto este TACHADO -->

<h2> <span style="color:#0089D6"> Contexto </span> </h1>

<p><br>

<p style="color:#A4B1CD;">En Esta arquitectura En este artículo se comparan tres opciones para conectar una red local a una red virtual (red virtual) de Azure. Para cada opción, hay disponible una arquitectura de referencia más detallada. </p>


<p><br>
<p><br>

<img src="https://learn.microsoft.com/en-us/azure/architecture/reference-architectures/hybrid-networking/images/vpn-gateway-multisite-connection-diagram.png" width="1000px">

<p><br>
<p><br>


<h1> <span style="color:#0089D6"> Flujo de trabajo de la arquitectura </span> </h1>

<p><br>
<p><br>


<h2> <span style="color:#0089D6"> Conexión VPN </span> </h2>


<p style="color:#A4B1CD;"> Una puerta de enlace VPN es un tipo de puerta de enlace de red virtual que envía tráfico cifrado entre una red virtual de Azure y una ubicación local. El tráfico cifrado pasa por la Internet pública.</p>

<p style="color:#A4B1CD;">Esta arquitectura es adecuada para aplicaciones híbridas en las que es probable que el tráfico entre el hardware local y la nube sea ligero, o que esté dispuesto a cambiar la latencia ligeramente extendida por la flexibilidad y la potencia de procesamiento de la nube.
</p>


<h2> <span style="color:#0089D6">Beneficios </span> </h2> 

<p><br>



<p style="color:#A4B1CD;"> - Requiere un dispositivo VPN local. </p>

<p style="color:#A4B1CD;">- Ancho de banda mucho mayor disponible; hasta 10 Gbps dependiendo del SKU de VPN Gateway. </p>

<p><br>

<h2> <span style="color:#0089D6">Conexión de Azure ExpressRoute </span> </h2> 

<p><br>

<p style="color:#A4B1CD;"> Las conexiones expressRoute utilizan una conexión privada y dedicada a través de un proveedor de conectividad de terceros. La conexión privada extiende la red local a Azure. </p>

<p style="color:#A4B1CD;">Esta arquitectura es adecuada para aplicaciones híbridas que ejecutan cargas de trabajo de misión crítica a gran escala que requieren un alto grado de escalabilidad.</p>
<p><br>

<p><br>

<img src="https://learn.microsoft.com/en-us/azure/architecture/reference-architectures/hybrid-networking/images/expressroute-connection-overview.png" alt="JuveYell" width="1100px">
<p><br>


<p><br>


<p><br>




<h1> <span style="color:#0089D6"> Beneficios  </span> </h1> 

<p><br>

<p style="color:#A4B1CD;">- Ancho de banda mucho mayor disponible; hasta 10 Gbps dependiendo del proveedor de conectividad.<p>
<p style="color:#A4B1CD;">- Latencias más bajas y consistentes en comparación con las conexiones típicas a través de Internet.<p>
<p style="color:#A4B1CD;">- Admite el escalado dinámico del ancho de banda para ayudar a reducir los costos durante los períodos de menor demanda. Sin embargo, no todos los - - proveedores de conectividad tienen esta opción.<p>
<p style="color:#A4B1CD;">- Puede permitir a su organización el acceso directo a las nubes nacionales, dependiendo del proveedor de conectividad.<p>
<p style="color:#A4B1CD;">- SLA de disponibilidad del 99,9% en toda la conexión.<p>

<p><br>
<p><br>
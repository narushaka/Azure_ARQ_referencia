<!-- los # o el h1 definen el tamano de la letra -->

<body bgcolor="#141D2B">

<div>
<p style = 'text-align:center;'>

<img src="https://www.svgrepo.com/show/353464/azure.svg" alt="JuveYell" width="300px">
</p>
</div>



<h1> <span style="color:#0089D6"> Arquitectura de disaster recovery regional </span> 


<!-- italic -->


<!-- genero espaciado copn el comando <p><br> -->


<p><br>



<!-- el ** define que le texto este en NEGRILLA O STRONG -->

<!-- el ~~ define que le texto este TACHADO -->

<h2> <span style="color:#0089D6"> Contexto</span> </h1>

<p><br>

<p style="color:#A4B1CD;">Las máquinas virtuales están físicamente separadas entre zonas y se crea una red virtual mediante equilibradores de carga en cada sitio. Estas ubicaciones están lo suficientemente cerca para la replicación de alta disponibilidad, por lo que las aplicaciones permanecen en ejecución aunque se produzca algún problema en las ubicaciones físicas.</p>


<p><br>
<p><br>

<img src="https://docs.microsoft.com/es-es/azure/architecture/solution-ideas/media/build-high-availability-into-your-bcdr-strategy.png" alt="JuveYell" width="500px">

<p><br>
<p><br>


<h2> <span style="color:#0089D6"> Analisis de la arquitectura</span> </h1>

<p><br>
<p><br>

<p style="color:#A4B1CD;">
1) Creación de un equilibrador de carga con redundancia de zona<br>
2) Creación de una subred de front-end<br>
3) Creación de una subred de base de datos<br>
4) Creación de máquinas virtuales en tres zonas de disponibilidad<br>
5) Configuración de una base de datos SQL con redundancia de zona<br>
6) Adición de máquinas virtuales al grupo de back-end del equilibrador de carga.<br>
7) Implementación de la aplicación en máquinas virtuales para obtener redundancia y alta disponibilidad</p>
<p><br>
<h2> <span style="color:#0089D6"> Componentes arquitectonicos</span> </h1>
<p><br>

<h3> <span style="color:#0089D6">Virtual machine de Azure</span> </h3>
<p><br>


<img src="https://4.bp.blogspot.com/-6kxXPrWRJgg/WQU0DaEYDsI/AAAAAAAAHmE/Je6tStW7R3kxuHDVEA3kImKH80hDm9DUACLcB/s1600/vm.png" alt="JuveYell" width="200px">
<p><br>

<p style="color:#A4B1CD;">Las máquinas virtuales de Azure permiten crear en cuestión de minutos recursos de proceso dedicados, que se pueden usar del mismo modo que un equipo de servidor o escritorio físico.</p>

<p><br>
<h3> <span style="color:#0089D6">Azure load Balancer</span> </h3>

<p><br>
<img src="https://www.freelogovectors.net/wp-content/uploads/2022/03/azure-load-balancer-logo_freelogovectors.net_.png" alt="JuveYell" width="150px">
<p><br>



<p style="color:#A4B1CD;"> Azure Load Balancer opera en la capa 4 del modelo Interconexión de sistemas abiertos (OSI). Es el único punto de contacto de los clientes. Load Balancer distribuye flujos de entrada que llegan al front-end del equilibrador de carga a las instancias del grupo de back-end. Estos flujos están de acuerdo con las reglas de equilibrio de carga y los sondeos de estado configurados. Las instancias del grupo de back-end pueden ser instancias de Azure Virtual Machines o de un conjunto de escalado de máquinas virtuales. </p>

<p style="color:#A4B1CD;"> Un equilibrador de carga público puede proporcionar conexiones de salida para máquinas virtuales dentro de la red virtual. Estas conexiones se realizan mediante la traducción de sus direcciones IP privadas a direcciones IP públicas. Las instancias públicas de Load Balancer se usan para equilibrar la carga del tráfico de Internet en las máquinas virtuales.</p>

<p><br>
<h3> <span style="color:#0089D6">Azure SQL</span> </h3>
<p><br>


<p><br>
<img src="https://www.freelogovectors.net/wp-content/uploads/2022/03/azure_sql_database_logo_freelogovectors.net_.png" alt="JuveYell" width="120px">
<p><br>



<p style="color:#A4B1CD;"> Azure SQL Database es un servicio de base de datos relacional totalmente administrado y siempre actualizado creado para la nube. Cree su próxima aplicación con la simplicidad y flexibilidad de una base de datos multimodelo que se escala para satisfacer la demanda. 
</p>








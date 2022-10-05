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

<h2> <span style="color:#0089D6"> Contexto z|z  </span> </h1>

<p><br>

<p style="color:#A4B1CD;">Esta arquitectura de referencia muestra una aplicación de microservicios implementada en Azure Kubernetes Service (AKS). Describe una configuración básica de AKS que puede ser el punto de partida para la mayoría de las implementaciones. Este artículo asume conocimientos básicos de Kubernetes. El artículo se centra principalmente en la infraestructura y las consideraciones de DevOps de la ejecución de una arquitectura de microservicios en AKS. Para obtener instrucciones sobre cómo diseñar microservicios, consulte Creación de microservicios en Azure..</p>


<p><br>
<p><br>

<img src="https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/containers/aks-microservices/images/aks.png" alt="JuveYell" width="1000px">

<p><br>
<p><br>


<h2> <span style="color:#0089D6"> Flujo de trabajo de la arquitectura </span> </h1>

<p><br>
<p><br>

<p style="color:#A4B1CD;"> La arquitectura consta de los siguientes componentes:</p>

<p style="color:#A4B1CD;">Azure Kubernetes Service (AKS). AKS es un clúster de Kubernetes administrado hospedado en la nube de Azure. Cuando se usa AKS, Azure administra el servicio de API de Kubernetes y solo necesita administrar los nodos del agente.</p>

<p style="color:#A4B1CD;"> Red virtual. De forma predeterminada, AKS crea una red virtual en la que se conectan los nodos del agente. Puede crear la red virtual primero para escenarios más avanzados, lo que le permite controlar cosas como la configuración de subred, la conectividad local y el direccionamiento IP. Para obtener más información, consulte Configuración de redes avanzadas en Azure Kubernetes Service (AKS).</p>

<p style="color:#A4B1CD;"> Ingreso. Un servidor de entrada expone rutas HTTP(S) a servicios dentro del clúster. Para obtener más información, consulte la sección API Gateway a continuación.</p>

<p style="color:#A4B1CD;">Azure Load Balancer. Después de crear un clúster de AKS, el clúster está listo para usar el equilibrador de carga. Luego, una vez que se implemente el servicio NGINX, el equilibrador de carga se configurará con una nueva IP pública que se enfrentará a su controlador de entrada. De esta manera, el equilibrador de carga enruta el tráfico de Internet a la entrada.</p>

<p style="color:#A4B1CD;"> Almacenes de datos externos. Los microservicios suelen ser sin estado y escribir estado en almacenes de datos externos, como Azure SQL Database o Cosmos DB.</p>

<p style="color:#A4B1CD;">Azure Active Directory. AKS usa una identidad de Azure Active Directory (Azure AD) para crear y administrar otros recursos de Azure, como los equilibradores de carga de Azure. Azure AD también se recomienda para la autenticación de usuarios en aplicaciones cliente.</p>

<p style="color:#A4B1CD;">Registro de contenedores de Azure. Utilice Container Registry para almacenar imágenes privadas de Docker, que se implementan en el clúster. AKS puede autenticarse con Container Registry mediante su identidad de Azure AD. Tenga en cuenta que AKS no requiere Azure Container Registry. Puede utilizar otros registros de contenedores, como Docker Hub.</p>

<p style="color:#A4B1CD;">Azure Pipelines. Azure Pipelines forma parte de azure DevOps Services y ejecuta compilaciones, pruebas e implementaciones automatizadas. También puede utilizar soluciones de CI/CD de terceros, como Jenkins.</p>

<p style="color:#A4B1CD;">Timón. Helm es un administrador de paquetes para Kubernetes, una forma de agrupar y generalizar objetos de Kubernetes en una sola unidad que se puede publicar, implementar, versionar y actualizar.</p>

<p style="color:#A4B1CD;">Azure Monitor. Azure Monitor recopila y almacena métricas y registros, telemetría de aplicaciones y métricas de plataforma para los servicios de Azure. Utilice estos datos para supervisar la aplicación, configurar alertas, paneles y realizar análisis de causa raíz de errores. Azure Monitor se integra con AKS para recopilar métricas de controladores, nodos y contenedores.</p>



<p><br>
<p><br>



<h1> <span style="color:#0089D6"> Componentes  </span> </h1> 

<p><br>

<h2> <span style="color:#0089D6"> Azure Pipelines  </span> </h2>

<p><br>

<img src="https://www.returngis.net/wp-content/uploads/2019/10/Azure-DevOps-Pipelines.png" alt="JuveYell" width="200px">
<p><br>



<p><br>

<p style="color:#A4B1CD;"> Herramienta para la automatizacion de commpilaciones y las implementaciones con Pipelines para poder dedicar menos tiempo a estos procesos y más a crear con la mejora continua (CI) y entrega continua (CD). Funciona con tu proveedor de Git preferido y puede implementarse en la mayoría de los servicios en la nube principales.</p>


<p><br>
<p><br>

<h2> <span style="color:#0089D6"> Azure Kubernetes Service (AKS)  </span> </h2>

<p><br>
<p><br>

<img src="https://24xsiempre.com/wp-content/uploads/2022/03/azure-container-service.png" alt="JuveYell" width="200px">

<p style="color:#A4B1CD;">Es la aplicacion  más rápida de comenzar a desarrollar e implementar aplicaciones nativas de la nube, con canalizaciones y barreras de protección integradas de código a nube. Obtenga administración y gobernanza unificadas para clústeres de Kubernetes locales, perimetrales y multinube. Interopere con los servicios de seguridad, identidad, administración de costos y migración de Azure.</p>

<p><br>
<p><br>

<h2> <span style="color:#0089D6"> Azure Cosmos DB  </span> </h2>

<p><br>
<p><br>

<img src="https://symbols.getvecta.com/stencil_27/54_key-vault.f497b9647f.svg" alt="JuveYell" width="200px">


<p><br>
<p><br>



<p style="color:#A4B1CD;"> Azure Cosmos DB es una base de datos NoSQL totalmente administrada para el desarrollo de aplicaciones modernas. Los tiempos de respuesta de milisegundos de un solo dígito y la escalabilidad automática e instantánea garantizan velocidad a cualquier escala. La continuidad del negocio está garantizada con disponibilidad respaldada por SLA y seguridad de nivel empresarial. El desarrollo de aplicaciones es más rápido y productivo gracias a la distribución de datos llave en mano en varias regiones en cualquier parte del mundo, las API de código abierto y los SDK para idiomas populares. Como servicio totalmente administrado, Azure Cosmos DB quita la administración de bases de datos de sus manos con administración automática, actualizaciones y revisiones. También maneja la administración de la capacidad con opciones de escalado automático y sin servidor rentables que responden a las necesidades de las aplicaciones para hacer coincidir la capacidad con la demanda.</p>



<p><br>

<h2> <span style="color:#0089D6"> Key Vault </span> </h2>

<p><br>
<p><br>

<img src="https://www.freelogovectors.net/wp-content/uploads/2022/03/azure_cosmos_db_logo_freelogovectors.net_-400x398.png" alt="JuveYell" width="200px">


<p><br>




<p style="color:#A4B1CD;"> Azure Key Vault permite a los suscriptores de Azure proteger y controlar claves criptográficas y otros secretos usados por aplicaciones y servicios en la nube. Azure Key Vault proporciona dos tipos de contenedores:</p>

<p style="color:#A4B1CD;"> Almacenes para guardar y administrar claves criptográficas, secretos, certificados y claves de cuentas de almacenamiento.
Grupo de HSM administrado para almacenar y administrar claves criptográficas respaldadas por HSM</p>
<p><br>
<p><br>
<p><br>



<h1> <span style="color:#0089D6"> Consideraciones </span> </h1>


<p><br>



<h2> <span style="color:#0089D6"> Diseño </span> </h2>


<p style="color:#A4B1CD;">  Esta arquitectura de referencia se centra en las arquitecturas de microservicios, aunque muchas de las prácticas recomendadas se aplican a otras cargas de trabajo que se ejecutan en AKS.</p>

<p><br>

<h2> <span style="color:#0089D6"> Microservicios </span> </h2>
</p>

<p><br>

<p style="color:#A4B1CD;">  Un microservicio es una unidad de código poco acoplada e independientemente desplegable. Los microservicios suelen comunicarse a través de API bien definidas y se pueden detectar a través de alguna forma de descubrimiento de servicios. El servicio siempre debe ser accesible incluso cuando las cápsulas se mueven. El objeto Kubernetes Service es una forma natural de modelar microservicios en Kubernetes.</p>

<p><br>

<h2> <span style="color:#0089D6"> Puerta de enlace api </span> </h2>

<p style="color:#A4B1CD;"> Las puertas de enlace de API son un patrón general de diseño de microservicios. Una puerta de enlace de API se encuentra entre los clientes externos y los microservicios. Actúa como un proxy inverso, enrutando las solicitudes de los clientes a los microservicios. También puede realizar varias tareas transversales, como autenticación, terminación SSL y limitación de velocidad. </p>



<p style="color:#A4B1CD;"> En Kubernetes, la funcionalidad de una puerta de enlace api es manejada principalmente por un controlador Ingress. Las consideraciones se describen en la sección Ingress. </p>
</p>

<p><br>

<h2> <span style="color:#0089D6"> Almacenamiento de datos </span> </h2>

</p>

<p><br>

<p style="color:#A4B1CD;">  En una arquitectura de microservicios, los servicios no deben compartir soluciones de almacenamiento de datos. Cada servicio debe administrar su propio conjunto de datos para evitar dependencias ocultas entre los servicios. La separación de datos ayuda a evitar el acoplamiento involuntario entre servicios, lo que puede ocurrir cuando los servicios comparten los mismos esquemas de datos subyacentes. Además, cuando los servicios administran sus propios almacenes de datos, pueden usar el almacén de datos adecuado para sus requisitos particulares. </p>






<p style="color:#A4B1CD;">  Evite almacenar datos persistentes en el almacenamiento de clúster local porque eso vincula los datos al nodo. En su lugar, use un servicio externo como Base de datos SQL de Azure o Cosmos DB. Otra opción es montar un volumen de datos persistente en una solución mediante Azure Disks o Azure Files.</p>

<p><br>
<p><br>


<h1> <span style="color:#0089D6">  Limitaciones de recursos </span> </h1>
</p>

<p><br>

<p style="color:#A4B1CD;">  La contención de recursos puede afectar a la disponibilidad de un servicio. Defina las restricciones de recursos para los contenedores, de modo que un solo contenedor no pueda abrumar los recursos del clúster (memoria y CPU). Para los recursos que no son contenedores, como subprocesos o conexiones de red, considere la posibilidad de usar el patrón de mamparos para aislar los recursos. </p>

<p style="color:#A4B1CD;">  Utilice cuotas de recursos para limitar el total de recursos permitidos para un espacio de nombres. De esa manera, el front-end no puede privar a los servicios de backend de recursos o viceversa.  </p>
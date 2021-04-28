# GKE-Terraform
Instalar GKE con Terraform


1.- Se debe crear una cuenta de Google Cloud Plataform:
    -Acceder a https://console.cloud.google.com
    -Elegir crear una cuenta, y luego dar click en "Para mi"
    -Agregar información personal,tarjeta de credito (GCP regala $300 por un año)
    
2.- Crear proyecto
    -Por defecto se debe tener uno, pero puede crear mas si es necesario.
    -En la parte superior izquierda se encuentran los proyectos, al dar click sobre el proyecto actual se te desplega una ventana con todos los proyectos que se han      creado.
    -Si dese crear un nuevo proyecto hay que dar click en la esquina superior derecha en la opción de proyectos, se coloca el nombre y se crea el proyecto
    
3.- Crear Service Account para el proyecto Terraform:
    -Seleccionar la opcion IAM & admin.
    -En IAM seleccionar la opcion service account
    -Seleccionar la opcion create service account, llenar los datos solicitados y dar los siguientes permisos al service account:
      Compute Admin
      Kubernetes Engine Admin
      Service Account User
      Service Networking Admin
      Storage Admin
    Una vez terminado el service account, debera aparecer en la lista, damos click en los tres puntitos de la seccion actions y se debe seleccionar create key,         selecciona JSON y posteriormente se le descargara la llave, llave que permitira a terraform conectar con GCP crear recursos.
    
    
    
4.- Activar las APIS de Google
    -Se deben activar las Apis de Google para el uso de cada producto, para esto se debe acceder al menu principal y seleccionar APIs & Services
    -En la parte super dar click en la opcion Enable APIS and Services.
    -Buscar la API del producto que se necesita activar y listo.
    -En este caso el API que necesita activar es la de fds
    

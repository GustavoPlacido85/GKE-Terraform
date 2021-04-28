# GKE-Terraform
Instalar GKE con Terraform


1.- Se debe crear una cuenta de Google Cloud Plataform:

    -Acceder a https://console.cloud.google.com
    -Elegir crear una cuenta, y luego dar click en "Para mi"
    -Agregar información personal,tarjeta de credito (GCP regala $300 por un año)
    
2.- Crear proyecto

    -Por defecto se debe tener uno, pero puede crear mas si es necesario.
    -En la parte superior izquierda se encuentran los proyectos, al dar click sobre el proyecto actual se te desplega una ventana con todos los proyectos que se        han creado.
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
    
    
5.- Instalar terraform

    Instalar la version terraform 0.12.5
    Para facilitar el manejo de versiones instalar tfswitch
        curl -L https://raw.githubusercontent.com/warrensbox/terraform-switcher/release/install.sh | bash
    Luego llamar el comando tfswitch en consola, seleccionar la version y listo
        Manual de instalacion https://medium.com/@warrensbox/how-to-manage-different-terraform-versions-for-each-project-51cca80ccece
    
6.- Instalar GKE

    Crear Bucket
    Crear un bucket en Storage con el nombre que deseas, el nombre debe ser unico.
    Editar gke/backend.tf
    Abrir el archivo gke/backend.tf
    Editar la opcion bucket, por el nombre de bucket que creaste en el paso anterior.
    En la opcion credentials añadir la direccion del archivo de credenciales que te descargaste al crear el service account.
    Editar gke/main.tf
    Abrir el archivo gke/main.tf
    Editar la opcion credentials con lo mismo que colocaste en el archivo backend.tf
    Editar el nombre del proyecto, por el que hayas creado en los pasos anteriores.
    
7.- Instalar Gcloud para obtener las credenciales

    Para linux instalar con:
        apt-get install gcloud
    Autenticarse con el correo que creo la cuenta de Google Cloud Plataform
        gcloud auth login
    Una vez instalado, dentro de la carpeta gke ejecutar los siguientes comandos:
        sudo terraform init
        sudo terraform apply
    Luego de instalar ejecutar el siguiente comando para traer las credenciales del Kubernertes creado
        gcloud container clusters get-credentials default-cloudgoec-course-gke --zone us-east4-a --project cloudgoec
        
8.- Instalar Kubectl para acceder al cluster

    Para instalar el kubectl ejecutar los siguientes comandos
        curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.15.0/bin/linux/amd64/kubectl
        chmod +x ./kubectl
        sudo mv ./kubectl /usr/local/bin/kubectl        
        
9.- Ver los nodos del cluster

        kubectl get nodes        
    
    
10.-Si desea eliminar todo lo creado con terraform ejecuta el siguiente comando
        
        sudo terraform destroy    
    

# solmar-k8s-config
Config for deploy Solmar backend on DockerDesktop

# Description

Instrucciones para deployar en local

  Requisitos:
  *   kubectl instalado.
  *   Un clúster de Kubernetes funcionando (como el de Docker Desktop).
  Instrucciones:
   1.  Clona el repositorio de configuración:
        git clone https://github.com/diurvan/solmar-k8s-config.git
        cd solmar-k8s-config
   2.  **(Paso único) Crea el Secreto de Kubernetes en tu clúster:**
        Necesitas crear un "secreto" que le permita a Kubernetes iniciar sesión en mi Docker Hub.
        Ejecuta el siguiente comando, reemplazando `<TU_TOKEN_AQUI>` con el token de acceso que te he proporcionado abajo.
   
        kubectl create secret docker-registry regcred --docker-server=https://index.docker.io/v1/ --docker-username=diurvan --docker-password=<TU_TOKEN_AQUI> --docker-email=tu@email.com
    
        *(Nota: El email no es crítico, puedes usar cualquiera)*.
    3.  **Despliega la aplicación:**
        Una vez creado el secreto, ya puedes desplegar todo como siempre.
        kubectl apply -k k8s/overlays/dev
   
   !Eso es todo! Kubernetes ahora usará el secreto `regcred` para autenticarse con Docker Hub y descargar las imágenes privadas. La aplicación estará disponible en `http://localhost:30577`

   *********************************************
   docker login -u diurvan
   dckr_pat_Vc5b9K2IjOHqV8bybLU7IO53WEI
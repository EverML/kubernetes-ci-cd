# Ejecutar el bash dentro de un container (pod) corriendo

```bash
kubectl exec -it NameDelPod bash
```
# Revisar detalles del pod

```bash
kubectl describe pod name_del_po
```



# Anotaciones Tutorial Kubernetes


Probando con:
 * VirtualBox 5.2 (No funciona tan bien con la 6.0 por el tema de las IP's dinámicas)
 * Minikube 1.5.1
 * Kubernetes v1.16.2 
 * Docker 18.09.9


# Parar Alterar version  de kubernetes,memoria, procesador
minikube start --memory 4000 --cpus 2 --kubernetes-version v1.11.10 



# Habilitar el addon del dashboard (deshabilitado por defecto)
minikube addons enable dashboard




# Para generar la imagen de docker.

```bash
docker build -t cicdtest .

docker tag cicdtest:latest <username>/cicdtest:latest

docker push <username>/cicdtest:latest

```




# Para montar dentro de un pod en kubernetes (Ejemplo minikube)
    minikube start
    
    
    kubectl create deployment nombreCualquiera --image=<username>/cicdtest:latest
    
    
    kubectl expose deployment nombreCualquiera --type=LoadBalancer --port=8081
    
    
    
    minikube service nombreCualquiera
    


# Para eliminar el servicio

    kubectl delete service nombreCualquiera
    
    kubectl delete deployment nombreCualquiera
    
    minikube stop


//Opcional
`minikube delete`

# Para hacer el reverse proxy
```bash

kubectl apply -f ingress.yaml
```
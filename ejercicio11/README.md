# Ejercicio 11


## Aplicando Descriptor de Kubernetes
Para aplicar el descriptor de Kubernetes, ejecutamos:

    kubectl apply -f deployment.yml
a
y luego para verificar revisamos con el comando 

    kubectl get all

Que retorna las 3 replicas creadas:

    NAME                              READY   STATUS    RESTARTS   AGE
    pod/passwordapi-59c98bb47-7d799   1/1     Running   0          4m58s       
    pod/passwordapi-59c98bb47-wcdl7   1/1     Running   0          4m58s       
    pod/passwordapi-59c98bb47-xdmjc   1/1     Running   0          4m58s       

    NAME                 TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)   AGE  
    service/kubernetes   ClusterIP   10.96.0.1    <none>        443/TCP   5m15s

    NAME                          READY   UP-TO-DATE   AVAILABLE   AGE  
    deployment.apps/passwordapi   3/3     3            3           4m58s

    NAME                                    DESIRED   CURRENT   READY   AGE
    replicaset.apps/passwordapi-59c98bb47   3         3         3       4m58s

## Verificar el funcionamiento 
Para verificar tomamos la terminar en modo interactivo por ejemplo del pod passwordapi-59c98bb47-7d799, para eso ejecutamos:

    kubectl exec -it passwordapi-59c98bb47-7d799 --  bash

 y luego ya dentro del pod ejecutamos:
 
    curl localhost:3000/password

Que retorna:

    root@passwordapi-59c98bb47-7d799:/usr/src/app# curl localhost:3000/password
    {"password":"!865BbGgLlFf"}
    

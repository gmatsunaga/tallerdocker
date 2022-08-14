# Ejercicio 14

## Aplicando Descriptor de Kubernetes
Para aplicar el descriptor de Kubernetes, ejecutamos:

    kubectl apply -f deployment.yml
a
y luego para verificar revisamos con el comando 

    kubectl get all

Que retorna las 3 replicas creadas corriendo por mas de 5 minutos:

NAME                               READY   STATUS    RESTARTS   AGE
pod/passwordapi-7b9d6dfd5f-hl8gf   1/1     Running   0          5m55s
pod/passwordapi-7b9d6dfd5f-jcx64   1/1     Running   0          5m55s
pod/passwordapi-7b9d6dfd5f-lktqx   1/1     Running   0          5m55s

NAME                 TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)   AGE
service/kubernetes   ClusterIP   10.96.0.1    <none>        443/TCP   6m17s

NAME                          READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/passwordapi   3/3     3            3           5m55s

NAME                                     DESIRED   CURRENT   READY   AGE
replicaset.apps/passwordapi-7b9d6dfd5f   3         3         3       5m55s


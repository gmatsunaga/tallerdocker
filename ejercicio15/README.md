# Ejercicio 15

## Aplicando Descriptor de Kubernetes
Para aplicar el descriptor de Kubernetes, ejecutamos:

    kubectl apply -f deployment.yml

NOTA: Como se observo que la respuesta /is-alive suele demorar aprox 3 segundos se llevo el timeout a 5 segundos y el periodo de chequeo a 10 segundos

Para verificar revisamos con el comando 

    kubectl get all

Que retorna la replicas creadas corriendo por mas de 3 minutos:

NAME                         READY   STATUS    RESTARTS   AGE
pod/pingapp-74579896-mr6bw   1/1     Running   0          3m31s

NAME                 TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)   AGE
service/kubernetes   ClusterIP   10.96.0.1    <none>        443/TCP   6m53s

NAME                      READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/pingapp   1/1     1            1           3m31s

NAME                               DESIRED   CURRENT   READY   AGE
replicaset.apps/pingapp-74579896   1         1         1       3m31s
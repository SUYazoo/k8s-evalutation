# Examen du 26 Mai 2023 : Evaluation Kubernetes (Yatté Kébé)

## Architecture du repo pour l'evaluation 

* redis (deploiement sur la base redis)
* redis-node (deploiement sur un serveur codé par l'évaluateur)

## Commandes lancées en Bash pour démarrer la communication :


```bash
kubectl apply -f kebe-redis-deployment.yaml
kubectl apply -f kebe-node-redis-deployment.yaml


kubectl apply -f kebe-node-redis-pod.yaml

kubectl apply -f kebe-redis-service.yaml
kubectl apply -f kebe-node-redis-service.yaml
```

## Verifications :

### Deploiements
```bash
kubectl get deployments | grep "kebe"
kebe-node-redis          4/4     4            4           
kebe-redis               1/1     1            1           
```

### Services 
```bash
kubectl get services | grep "kebe"
kebe-node-redis-service       LoadBalancer   10.3.127.140   141.95.163.93    5000:30007/TCP   
kebe-redis-service            LoadBalancer   10.3.137.190   141.95.163.59    6379:30822/TCP   
```

### Pods
```bash
$ kubectl get services | grep "kebe"
kebe-node-redis                           1/1     Running            0             
kebe-node-redis-b8fdd5fcc-6nwlt           1/1     Running            0             
kebe-node-redis-b8fdd5fcc-74f84           1/1     Running            0             
kebe-node-redis-b8fdd5fcc-88kjz           1/1     Running            0             
kebe-node-redis-b8fdd5fcc-dk9r9           1/1     Running            0             
kebe-redis-7c77d49576-nq29x               1/1     Running            0             
```

### Test d'un pod :
```bash
$ kubectl logs kebe-node-redis-b8fdd5fcc-6nwlt  
redis connected to redis://kebe-redis-service:6379
listening at http://localhost:5000
```

### Test de l'adresse IP Externe délivrée pour le service node redis :
```141.95.163.93:5000```
It is working, good job







# Домашнее задание к занятию «Kubernetes. Часть 1»

## Выполнил Савицкий Андрей

### Задание 1

**Выполните действия:**

1. Запустите Kubernetes локально, используя k3s или minikube на свой выбор.
1. Добейтесь стабильной работы всех системных контейнеров.

#### Скриншот результата выполнения команды kubectl get po -n kube-system:

![Задание 1](https://github.com/user-attachments/assets/559300ac-4709-432b-b56d-546ba417845a)

------
### Задание 2


Есть файл с деплоем:

```
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: redis
spec:
  selector:
    matchLabels:
      app: redis
  replicas: 1
  template:
    metadata:
      labels:
        app: redis
    spec:
      containers:
      - name: master
        image: bitnami/redis
        env:
         - name: REDIS_PASSWORD
           value: password123
        ports:
        - containerPort: 6379
```

------
**Выполните действия:**

1. Измените файл с учётом условий:

 * redis должен запускаться без пароля;
 * создайте Service, который будет направлять трафик на этот Deployment;
 * версия образа redis должна быть зафиксирована на 6.0.13.

2. Запустите Deployment в своём кластере и добейтесь его стабильной работы.

#### Получившийся файл:

```
apiVersion: v1 
kind: Service 
metadata: 
  name: redis 
spec: 
  selector: 
    app: redis 
  ports: 
    - protocol: TCP 
      port: 6379 
      targetPort: 6379
``` 

------
### Задание 3 с командами:

 *Напишите команды kubectl для контейнера из предыдущего задания:*

 - выполнения команды ps aux внутри контейнера:

   `sudo kubectl exec -it redis-79c8d44f9c-hwnsp -- ps aux` 
 - просмотра логов контейнера за последние 5 минут:

   `sudo kubectl logs --since=5m redis-79c8d44f9c-hwnsp` 
 - удаления контейнера:

   `sudo kubectl delete -f redis.yaml && sudo kubectl delete -f redis_service.yaml`
 - проброса порта локальной машины в контейнер для отладки:

   `sudo kubectl port-forward pod/redis-79c8d44f9c-hwnsp 54321:6379`

---

### Задание 4*

Есть конфигурация nginx:

```
location / {
    add_header Content-Type text/plain;
    return 200 'Hello from k8s';
}
```

**Выполните действия:**

1. Напишите yaml-файлы для развёртки nginx, в которых будут присутствовать:

 - ConfigMap с конфигом nginx;
 - Deployment, который бы подключал этот configmap;
 - Ingress, который будет направлять запросы по префиксу /test на наш сервис.

2. В качестве решения пришлите получившийся файл.

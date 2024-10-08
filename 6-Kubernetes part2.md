# Домашнее задание к занятию «Kubernetes. Часть 2»

## Выполнил Савицкий Андрей

### Задание 1

**Выполните действия:**

1. Создайте свой кластер с помощью kubeadm.
1. Установите любой понравившийся CNI плагин.
1. Добейтесь стабильной работы кластера.

#### Cкриншот результата выполнения команды `kubectl get po -n kube-system`:

![Задание 1](https://github.com/user-attachments/assets/4ae0b7d1-57df-4075-9494-50f837677a90)


---

### Задание 2

Есть файл с деплоем:

```yaml
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
**Выполните действия:**

1. Создайте Helm Charts.
1. Добавьте в него сервис.
1. Вынесите все нужные, на ваш взгляд, параметры в `values.yaml`.
1. Запустите чарт в своём кластере и добейтесь его стабильной работы.

#### Скриншот вывода команды `helm get manifest <имя_релиза>`:

![Задание 2](https://github.com/user-attachments/assets/363160a2-fc43-4011-84c7-5e5f46aa1fae)

---

### Задание 3*

1. Изучите [документацию](https://kubernetes.io/docs/concepts/storage/volumes/#hostpath) по подключению volume типа hostPath.
1. Дополните деплоймент в чарте подключением этого volume.
1. Запишите что-нибудь в файл на сервере, подключившись к поду с помощью `kubectl exec`, и проверьте правильность подключения volume.

В качестве ответа пришлите получившийся yaml-файл.

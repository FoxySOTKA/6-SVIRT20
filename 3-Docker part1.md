# Домашнее задание к занятию «Docker. Часть 1»

## Выполнил Савицкий Андрей

### Задание 1 

Чем контейнеризация отличается от виртуализации?

#### Ответ:
Контейнеризация отличается от виртуализации тем, что контейнер - это изолированная среда, которая для изоляции использует возможности не железа, а операционной системы хоста, так называемое пространство имён. Контейнер использует ядро хостовой ОС для обработки данных, без ограничения процессорного времени и памяти. В свою очередь, виртуальная машина полностью изолирует средствами процессора (технологии Intel, AMD, VMX) и системное ядро, и программные модули, и все библиотеки от хостовых. А по процессорному времени и памяти предоставляются строго ограниченные ресурсы.  

---

### Задание 2 

* Установите Docker.

   Скриншот:

  ![Задание 2](https://github.com/user-attachments/assets/0460d81e-d7ba-461c-bb13-eda626a3da19)

---

### Задание 3

* Запустите образ hello-world.

   Скриншот:

  ![Задание 3](https://github.com/user-attachments/assets/03bd2f4a-e460-4604-8098-0492be71cafa)

---

### Задание 4 

* Удалите образ hello-world.

   Скриншот:

  ![Задание 4](https://github.com/user-attachments/assets/7f397c85-da18-4b09-9391-d5e9236d1bca)

---

### Задание 5*

1. Найдите в Docker Hub образ apache и запустите его.
1. Приложите:
 * скриншоты сетевых настроек вашей виртуальной машины;
 * скриншоты работающих контейнеров;
 * скриншот браузера, где вы открыли дефолтную страницу вашего apache внутри контейнера.

---

### Задание 6*

1. Создайте свой Docker образ с Apache2 и подмените стандартную страницу index.html на страницу, содержащую ваши ФИО.
1. Приложите:
 * скриншот содержимого Dockerfile;
 * скриншот браузера, где apache2 из вашего контейнера выводит ваши ФИО.

# Домашнее задание к занятию «Введение в Terraform»

### Чек-лист готовности к домашнему заданию

Скачайте и установите **Terraform** версии ~>1.8.4 . Приложите скриншот вывода команды ```terraform --version```.

![img](https://github.com/SeNike/Study_24/blob/main/03.Terraform/1.png)
   


### Задание 1

1. Перейдите в каталог [**src**](https://github.com/netology-code/ter-homeworks/tree/main/01/src). Скачайте все необходимые зависимости, использованные в проекте. 
2. Изучите файл **.gitignore**. В каком terraform-файле, согласно этому .gitignore, допустимо сохранить личную, секретную информацию?(логины,пароли,ключи,токены итд)

-  ОТВЕТ: personal.auto.tfvars - файл для хранения секретов

   
4. Выполните код проекта. Найдите  в state-файле секретное содержимое созданного ресурса **random_password**, пришлите в качестве ответа конкретный ключ и его значение.

-  ОТВЕТ: "result": "eqvI5ZzVnQqLq18V"
   
6. Раскомментируйте блок кода, примерно расположенный на строчках 29–42 файла **main.tf**.
Выполните команду ```terraform validate```. Объясните, в чём заключаются намеренно допущенные ошибки. Исправьте их.

ОТВЕТ:
 - Каждый блок раздела ресурсов должениметь 2 лейбла (тип, имя)
 - Имя ресурса должно начинаться с буквы или нижнего подчеркивания
 - Ресурс "random_string_FAKE" не декларирован в корневом модуле
 - Объект не имеет аргументов, вложенных блоков или аттрибутов с именем "resulT"  

8. Выполните код. В качестве ответа приложите: исправленный фрагмент кода и вывод команды ```docker ps```.

![img](https://github.com/SeNike/Study_24/blob/main/03.Terraform/2.png)

![img](https://github.com/SeNike/Study_24/blob/main/03.Terraform/3.png)



10. Замените имя docker-контейнера в блоке кода на ```hello_world```. Не перепутайте имя контейнера и имя образа. Мы всё ещё продолжаем использовать name = "nginx:latest". Выполните команду ```terraform apply -auto-approve```.
Объясните своими словами, в чём может быть опасность применения ключа  ```-auto-approve```. Догадайтесь или нагуглите зачем может пригодиться данный ключ? В качестве ответа дополнительно приложите вывод команды ```docker ps```.

- ОТВЕТ: Опасность применения ключа -auto-approve в том, что изменения выполняются сразу без запроса. Данный ключ может использоваться в скриптах или прочих автоматизациях для их успешного прохождения.

![img](https://github.com/SeNike/Study_24/blob/main/03.Terraform/4.png)

12. Уничтожьте созданные ресурсы с помощью **terraform**. Убедитесь, что все ресурсы удалены. Приложите содержимое файла **terraform.tfstate**.

![img](https://github.com/SeNike/Study_24/blob/main/03.Terraform/tfstate.png)

13. Объясните, почему при этом не был удалён docker-образ **nginx:latest**. Ответ **ОБЯЗАТЕЛЬНО НАЙДИТЕ В ПРЕДОСТАВЛЕННОМ КОДЕ**, а затем **ОБЯЗАТЕЛЬНО ПОДКРЕПИТЕ** строчкой из документации [**terraform провайдера docker**](https://docs.comcloud.xyz/providers/kreuzwerker/docker/latest/docs).  (ищите в классификаторе resource docker_image )

- ОТВЕТ: Образ не был удален из-за ключа keep_locally = true

keep_locally (Boolean) If true, then the Docker image won't be deleted on destroy operation. If this is false, it will delete the image from the docker local storage on destroy operation.


------

## Дополнительное задание (со звёздочкой*)

### Задание 2*

6. Зайдите на вашу ВМ , подключитесь к контейнеру и проверьте наличие секретных env-переменных с помощью команды ```env```. Запишите ваш финальный код в репозиторий.

![img](https://github.com/SeNike/Study_24/blob/main/03.Terraform/6.png)

[Скрипт Terraform](https://github.com/SeNike/example_terraform_1/blob/main/main.tf)

### Задание 3*
1. Установите [opentofu](https://opentofu.org/)(fork terraform с лицензией Mozilla Public License, version 2.0) любой версии
2. Попробуйте выполнить тот же код с помощью ```tofu apply```, а не terraform apply.

![img](https://github.com/SeNike/Study_24/blob/main/03.Terraform/8.png)

- ОТВЕТ: Серсия установленного OpenTofu не соответствовала минимальной версии в main.tf
После уменьшения версии до 1.8.1 в скрипте, tofu apply прошел успешно.

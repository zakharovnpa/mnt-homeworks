# Домашнее задание к занятию "8.4 Работа с Roles"

## Подготовка к выполнению
1. Создайте два пустых публичных репозитория в любом своём проекте: kibana-role и filebeat-role.
2. Добавьте публичную часть своего ключа к своему профилю в github.

## Основная часть

Наша основная цель - разбить наш playbook на отдельные roles. Задача: сделать roles для elastic, kibana, filebeat и написать playbook для использования этих ролей. Ожидаемый результат: существуют два ваших репозитория с roles и один репозиторий с playbook.

1. Создать в старой версии playbook файл `requirements.yml` и заполнить его следующим содержимым:
   ```yaml
   ---
     - src: git@github.com:netology-code/mnt-homeworks-ansible.git
       scm: git
       version: "2.0.0"
       name: elastic 
   ```
2. При помощи `ansible-galaxy` скачать себе эту роль.
```ps
root@PC-Ubuntu:~/ansible-learning/yandex-cloud/Epsilon/Galaxy# ansible-galaxy install -r requirements.yml -p elasticsearch_role
Starting galaxy role install process
- extracting elastic to /root/ansible-learning/yandex-cloud/Galaxy/elasticsearch_role/elastic
- elastic (2.1.4) was installed successfully

```

3. Создать новый каталог с ролью при помощи `ansible-galaxy role init kibana-role`.
```ps
root@PC-Ubuntu:~/ansible-learning/yandex-cloud/Galaxy# ansible-galaxy role init kibana_role
- Role kibana_role was created successfully
root@PC-Ubuntu:~/ansible-learning/yandex-cloud/Galaxy# 
root@PC-Ubuntu:~/ansible-learning/yandex-cloud/Galaxy# ls -l
итого 28
drwxr-xr-x  3 root root 4096 фев 20 21:06 elasticsearch_role
drwxr-xr-x  3 root root 4096 фев 19 06:21 inventory
drwxr-xr-x 10 root root 4096 фев 20 21:11 kibana_role
-rw-r--r--  1 root root  530 фев 20 20:35 README.md
-rw-r--r--  1 root root  121 фев 20 20:36 requirements.yml
-rw-r--r--  1 root root 3012 фев 19 16:16 site.yml
drwxr-xr-x  2 root root 4096 фев 19 22:01 templates


```

4. На основе tasks из старого playbook заполните новую role. Разнесите переменные между `vars` и `default`. 


5. Перенести нужные шаблоны конфигов в `templates`.


6. Создать новый каталог с ролью при помощи `ansible-galaxy role init filebeat-role`.
```ps
root@PC-Ubuntu:~/ansible-learning/yandex-cloud/Galaxy# ansible-galaxy role init filebeat_role
- Role filebeat_role was created successfully
root@PC-Ubuntu:~/ansible-learning/yandex-cloud/Galaxy# 
root@PC-Ubuntu:~/ansible-learning/yandex-cloud/Galaxy# ls -l
итого 32
drwxr-xr-x 10 root root 4096 фев 20 21:12 elasticsearch_role
drwxr-xr-x 10 root root 4096 фев 20 21:13 filebeat_role
drwxr-xr-x  3 root root 4096 фев 19 06:21 inventory
drwxr-xr-x 10 root root 4096 фев 20 21:11 kibana_role
-rw-r--r--  1 root root  530 фев 20 20:35 README.md
-rw-r--r--  1 root root  121 фев 20 20:36 requirements.yml
-rw-r--r--  1 root root 3012 фев 19 16:16 site.yml
drwxr-xr-x  2 root root 4096 фев 19 22:01 templates

```

7. На основе tasks из старого playbook заполните новую role. Разнесите переменные между `vars` и `default`. 



8. Перенести нужные шаблоны конфигов в `templates`.
9. Описать в `README.md` обе роли и их параметры.
10. Выложите все roles в репозитории. Проставьте тэги, используя семантическую нумерацию.
11. Добавьте roles в `requirements.yml` в playbook.
12. Переработайте playbook на использование roles.
13. Выложите playbook в репозиторий.
14. В ответ приведите ссылки на оба репозитория с roles и одну ссылку на репозиторий с playbook.

## Необязательная часть

1. Проделайте схожие манипуляции для создания роли logstash.
2. Создайте дополнительный набор tasks, который позволяет обновлять стек ELK.
3. Убедитесь в работоспособности своего стека: установите logstash на свой хост с elasticsearch, настройте конфиги logstash и filebeat так, чтобы они взаимодействовали друг с другом и elasticsearch корректно.
4. Выложите logstash-role в репозиторий. В ответ приведите ссылку.

---

### Как оформить ДЗ?

Выполненное домашнее задание пришлите ссылкой на .md-файл в вашем репозитории.

---

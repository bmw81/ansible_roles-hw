# Домашнее задание к занятию 3 "`Работа с roles`" - `Белов Михаил`

## Подготовка к выполнению

1. Необязательно. Познакомьтесь с [LightHouse](https://youtu.be/ymlrNlaHzIY?t=929).
2. Создайте два пустых публичных репозитория в любом своём проекте: vector-role и lighthouse-role.
3. Добавьте публичную часть своего ключа к своему профилю на GitHub.


## Основная часть
Ваша цель — разбить ваш playbook на отдельные roles.

Задача — сделать roles для ClickHouse, Vector и LightHouse и написать playbook для использования этих ролей.

Ожидаемый результат — существуют три ваших репозитория: два с roles и один с playbook.

### Что нужно сделать

1. Создайте в старой версии playbook файл `requirements.yml` и заполните его содержимым:
```
---
  - src: git@github.com:AlexeySetevoi/ansible-clickhouse.git
    scm: git
    version: "1.13"
    name: clickhouse 
```
Ссылка на [requirements.yml](/playbook/requirements.yml)

2. При помощи ansible-galaxy скачайте себе эту роль.
```
cd ./playbook
ansible-galaxy install -r requirements.yml -p roles
```
![Clickhouse role install](/img/clickhouse_role_install.png)

3. Создайте новый каталог с ролью при помощи `ansible-galaxy role init ./roles/vector-role`.

![Init vector-role](/img/init_vector-role.png)

4. На основе tasks из старого playbook заполните новую role. Разнесите переменные между `vars` и `default`.

5. Перенести нужные шаблоны конфигов в templates.

[Содержимое директории vector-role](/playbook/roles/vector-role/)

6. Опишите в README.md обе роли и их параметры. Пример качественной документации ansible role [по ссылке](https://github.com/cloudalchemy/ansible-prometheus).

[README для clickhouse](/playbook/roles/clickhouse/README.md)

[README для vector-role](/playbook/roles/vector-role/README.md)

7. Повторите шаги 3–6 для LightHouse. Помните, что одна роль должна настраивать один продукт.

![Init lighthouse-role](/img/init_lighthouse-role.png)

[Содержимое директории lighthouse-role](/playbook/roles/lighthouse-role/)

[README для lighthouse-role](/playbook/roles/lighthouse-role/README.md)

`В задании не указано, но исходя из структуры следует создать role и для Nginx:`

```
ansible-galaxy role init ./roles/nginx-role
```

8. Выложите все roles в репозитории. Проставьте теги, используя семантическую нумерацию. Добавьте roles в requirements.yml в playbook.

[Файл requirements.yml](/playbook/requirements.yml)

9. Переработайте playbook на использование roles. Не забудьте про зависимости LightHouse и возможности совмещения `roles` с `tasks`

10. Выложите playbook в репозиторий.

11. В ответе дайте ссылки на оба репозитория с roles и одну ссылку на репозиторий с playbook.

[Vector Role](https://github.com/bmw81/vector-role#)

[Nginx Role](https://github.com/bmw81/nginx-role)

[Lighthouse Role](https://github.com/bmw81/lighthouse-role)
---
title: Coreprotect
description: Инструкция по эксплуатации
published: 0
date: 2024-01-25T12:14:19.312Z
tags: 
editor: markdown
dateCreated: 2024-01-24T11:20:56.398Z
---

# Общее
CoreProtect - плагин на запись изменений мира в базу данных (sqlite или mysql).


# Команды
В плагине присутствуют такие команды, как:
## /co inspect
Кратко: /co i
Переход в "режим инспектора". Позволяет на ЛКМ смотреть смотреть такие действия, как поломка/установка блока, а на ПКМ - транзакции с блоком, типо вещей в сундуке

## /co lookup
Кратко: /co l

## /co near
Команда для просмотра действий в радиусе 10 блоков от вас. Представляет собой по сути
`/co lookup r:10`

## /co rollback
Команда для отмены определённых действий 
## /co restore
Восстановить действия из бд. Действие обратное rollback
## /co undo
Отменить действие, влияющее на мир. То есть rollback или restore

# Выбираем записи
У команд lookup, rollback, restore есть возможность выбирать разные параметры поиска записей в бд.
Доступны следущие параметры:
## user
Кратко: u
`/co lookup r:10 u:username`
Пользователь, чьи действия искать.
Тем, от лица которого совершается действия может быть не только игрок 

## action
Кратко: a
`/co lookup r:10 a:-item`
Действия которые искать 

## include
Кратко: i
Предмет поиска. 
> В старых версиях плагина именуется block 
Кратко: b
{.is-info}

# Пользователи:
Не все действия совершают игроки, по крайней мере не на прямую. 
В CoreProtect помимо игровов действия могут совершать:
## Игрок
Игрок может совершать все действия в CoreProtect
## Моб
Мобы могут ломать блоки и убивать. 
Запись `#моб убил #моб` (самого себя) 
Означает смерть от удушья
## #tnt 
Взрывы динамита

## #[TNT]Username
TNT, активированный игроком Username
## #creeper
Взрывв крипера
## #[creeper]Username
Крипер, активированный игроком Username
## #fire
## #ender_crystal
## #physics 
## #gravity

# Действия

## item
### +item
### -item
## container
### -container
### +container
## block
### -block
### +block
## kill
## session
### -session
### +session
## text
## chat
## command

# Полезные примеры команд:
## Выявить виновника пожара
```/co lookup a:+block i:fire e:#fire r:20 t:2d```

## Взаимодействия с незеритовым шлемом
```/co lookup r:#global t:2d i:netherite_helmet u:username```

## Откат взрывов грифера на всём сервере 
```/co rollback r:#global t:2d u:#[TNT]username e:tnt``` 


## Превышени лимита новичка
```/co rollback r:#global t:2d i:netherite_helmet u:username```

# Домашнее задание к занятию 1.  «Введение в виртуализацию. Типы и функции гипервизоров. Обзор рынка вендоров и областей применения»


## Как сдавать задания

Обязательны к выполнению задачи без звёздочки. Их нужно выполнить, чтобы получить зачёт и диплом о профессиональной переподготовке.

Задачи со звёздочкой (*) — это дополнительные задачи и/или задачи повышенной сложности. Их выполнять не обязательно, но они помогут вам глубже понять тему.

Домашнее задание выполняйте в файле readme.md в GitHub-репозитории. В личном кабинете отправьте на проверку ссылку на .md-файл в вашем репозитории.

Любые вопросы по решению задач задавайте в чате учебной группы.

---

## Важно

Перед отправкой работы на проверку удаляйте неиспользуемые ресурсы.
Это нужно, чтобы не расходовать средства, полученные в результате использования промокода.

Подробные рекомендации [здесь](https://github.com/netology-code/virt-homeworks/blob/virt-11/r/README.md).

---

## Задача 1

Опишите кратко, в чём основное отличие полной (аппаратной) виртуализации, паравиртуализации и виртуализации на основе ОС.
```При полной аппаратной виртуализации используется специализированный гипервизор к примеру vmware esxi и ресурсы на аппаратном уровне предоставляются гостевой ос напрямую.
В паравиртуализации гостевая машина взаимодействует с ресурсами через api гипервизора.
Виртуализация на уровне ос - гостевая машина выполняется как отдельный процесс в ОС.
```

## Задача 2

Выберите один из вариантов использования организации физических серверов в зависимости от условий использования.

Организация серверов:

- физические сервера,
- паравиртуализация,
- виртуализация уровня ОС.

Условия использования:

- высоконагруженная база данных, чувствительная к отказу; 
```кластер vmware esxi с выскопроизводительным схд
```
- различные web-приложения;
``` виртуализация уровня ос или как вариант контейнеры
```
- Windows-системы для использования бухгалтерским отделом; 
```кластер vmware esxi если есть или microsoft hyper-v
```
- системы, выполняющие высокопроизводительные расчёты на GPU.vmware esxi т.к есть поддержка gpu

Опишите, почему вы выбрали к каждому целевому использованию такую организацию.

## Задача 3

Выберите подходящую систему управления виртуализацией для предложенного сценария. Детально опишите ваш выбор.

Сценарии:

1. 100 виртуальных машин на базе Linux и Windows, общие задачи, нет особых требований. Преимущественно Windows based-инфраструктура, требуется реализация программных балансировщиков нагрузки, репликации данных и автоматизированного механизма создания резервных копий.
```
кластер vmware на трех серверах hp gen10 двухпроцессорные по 24 ядра на процессор, память 256гигабайт. схд hp nimble af40, сервера напрямую подключаются по fc 16Gbit локальная сеть две циски 9300 в стеке, сервера подлкючаются 10 гигабитными адаптерами. Управление vmware vsphere, резервное копирование veeam backup минимум три сервера т.к один сервер не успеет сделать бекапы за ночь.
```
3. Требуется наиболее производительное бесплатное open source-решение для виртуализации небольшой (20-30 серверов) инфраструктуры на базе Linux и Windows виртуальных машин.
```proxmox ve сервера можно взять попроще и схд достаточно hp msa 2050/2060 если нет тяжелых баз данных можно использовать обычные диски не ssd
```
4. Необходимо бесплатное, максимально совместимое и производительное решение для виртуализации Windows-инфраструктуры.
аналогично proxmox ve
5. Необходимо рабочее окружение для тестирования программного продукта на нескольких дистрибутивах Linux.
proxmox ve дистрибутивы в lxc контейнерах

## Задача 4

Опишите возможные проблемы и недостатки гетерогенной среды виртуализации (использования нескольких систем управления виртуализацией одновременно) и что необходимо сделать для минимизации этих рисков и проблем. Если бы у вас был выбор, создавали бы вы гетерогенную среду или нет? Мотивируйте ваш ответ примерами.
```Первая проблема персонал, кто это будет поддерживать.
Чем сложнее система тем больше необхдимо специалистов.
Вторая проблема - резервное копирование. Для каждой системы виртуализации необходима своя.
Третья проблема - разная поддержка оборудования, если с vmware все относительно понятно есть матрицы совместимости и т.д, то в opensource решениях все не так очевидно.
И четвертая проблема - поддержка и документация
```


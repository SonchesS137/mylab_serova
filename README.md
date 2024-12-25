# mylab_serova

### Лабораторная работа №1 "планировщик задач cron"

### Что важно знать?
Cron (Command Run ON) — Если подробнее, то это утилита, позволяющая выполнять скрипты на сервере в назначенное время с заранее определенной периодичностью.
Вам предстоит сделать вывод таймера на экран с помошью crontab

### Задача

1. Для начала создайте файл `script.bash`
  
2. Реализуйте с помощью cron запись текста "Happy New Year!" в `script.bash`.

   Небольшая памятка по использованию `crontab`:

   TIME/SCRIPT/PATH
   
```
* * * * * command(s)
- - - - -
| | | | |
| | | | ----- Day of week (0 - 7) (Sunday=0 or 7)
| | | ------- Month (1 - 12)
| | --------- Day of month (1 - 31)
| ----------- Hour (0 - 23)
------------- Minute (0 - 59)
```
! не забудьте проверить работу программы и вставить скрины !

  3. Теперь вам предстоит реализовать таймер, также с помощью `cron`.

     Для этого создайте файл:
     
     `time.bash`

     Внутри файла вставьте код, считающий время до Нового года:

```
#!/bin/bash

print_date () {
        day=$(date +%e)
        hour=$(date +%H)
        minutes=$(date +%M)
        seconds=$(date +%S)
        let now_d=31-$day
        let now_h=23-$hour
        let now_m=59-$minutes
        let now_s=60-$seconds
    echo -e "\033[93m HAPPY NEW YEAR IN: $now_d days $now_h hours $now_m minutes $now_s seconds"

}

print_date #Вызов функции
```
  При желании вы можете модифицировать код, написав свою функцию или изменив внешний облик вывода с помощью colors.
  
4. Проверьте наличие `Homebrew` и при необходимости загрузите его на ваш компьютер.

  Для вывода результатов работы файла в отдельном окне воспользуемся `xterm`.

  ```
brew install xterm
```

5. Создайте bash файл, который будет использоваться для открытия основного скрипта.

Например:

`touch run.bash`

6. С помощью cron и crontab поставьте исполнение кода из файла каждую минуту и проверьте исправность работы.

!!! Не забудьте в созданном файле crontab указать правильный путь к файлу исполнителю `time.bash`, в нашем примере это - `run.bash`

В случае правильного решения лабораторной работы, на вашем компьютере будет всплывающее окно с временем, которое показывает сколько дней, часов, минут и секунд остается до нового года.
(Проверить верность времени вы можете с помощью онлайн таймеров в браузере.)

7. Можете поэкспериментировать с внешним видом открывающегося файла, а также временем исполнения задач в коде crontab.

### Решение

![Снимок экрана 2024-12-25 в 23 36 59](https://github.com/user-attachments/assets/c5270e29-da66-4999-94c9-850153c6ff4f)

![Снимок экрана 2024-12-25 в 23 18 48](https://github.com/user-attachments/assets/09b2bd12-779d-444c-a659-f110b64be32e)

![Снимок экрана 2024-12-25 в 23 26 17](https://github.com/user-attachments/assets/616dc7bc-66ea-4624-ada7-711168ea52e1)

![Снимок экрана 2024-12-25 в 23 29 33](https://github.com/user-attachments/assets/5cb7fc5d-7e89-4c00-9e9a-26574902cc4e)

![Снимок экрана 2024-12-25 в 23 36 08](https://github.com/user-attachments/assets/78e18961-871e-4df2-8fcb-8aa3f0d5f40c)

### Источники

https://timeweb.com/ru/community/articles/chto-takoe-cron

https://help.ubuntu.ru/wiki/cron

https://crontab.guru/#5_3_2_*_*

https://jino.ru/journal/articles/cron-commands/

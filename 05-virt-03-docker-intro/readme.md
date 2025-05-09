## Задача 1

![Screenshot][def screenshot]

[def screenshot]: <Screenshot 2025-05-08 at 4.57.23 PM.png>

https://hub.docker.com/repository/docker/miriam0010/custom-nginx/general

## Задача 2

![Screenshot][def screenshot1]

[def screenshot1]: <Screenshot 2025-05-09 at 4.55.10 PM.png>

## Задача 3

![Screenshot][def screenshot2]

[def screenshot2]: <Screenshot 2025-05-09 at 5.12.38 PM.png>

Он остановился, т.к. мы отправили ему сигнал через ctrl-c, nginx(единственный демон, который работает в контейнере) получает прерывание. 

![Screenshot][def screenshot3]

[def screenshot3]: <Screenshot 2025-05-09 at 5.17.51 PM.png>

Зашел в контейнер, поставил vim.

![Screenshot][def screenshot4]

[def screenshot4]: <Screenshot 2025-05-09 at 5.20.02 PM.png>

Действия со сменой портов. 
Суть проблемы: мы заменили порт nginx на 81, теперь ранее сделаный проброс портов 80-8080 не работает, т.к. 80й порт не используется.

Удаление запущенного контейнера:
![Screenshot][def screenshot5]

[def screenshot5]: <Screenshot 2025-05-09 at 7.21.00 PM.png>

## Задача 4

Скриншот со всеми шагами. Centos latest не работает, провозился с этой ерундой. Нужно указывать конкретную версию - поставил седьмую.

![Screenshot][def screenshot6]

[def screenshot6]: <Screenshot 2025-05-09 at 9.24.14 PM.png>

## Задача 5

1 - потому что у docker есть приоретизация имен - compose.yaml имеет высший приоритет.
Второй yaml я подключил через include.

![Screenshot][def screenshot7]

[def screenshot7]: <Screenshot 2025-05-09 at 9.39.02 PM.png>

Мне для registry пришлось поменять порт на 5001, какая-то системная утилита сидела на этом порту. Не критично, надеюсь?
Для portainer тоже не взлетело все "само". Я убрал пункт, который с хоста берет порты напрямую(думаю это не имеет значения) и явно прописал порписал порт. Думаю это все из-за macos. 

Доступность custom-nginx:

![Screenshot][def screenshot11]

[def screenshot11]: <Screenshot 2025-05-09 at 10.43.32 PM.png>

Тут все открыл, произвел и задеплоил:

![Screenshot][def screenshot8]

[def screenshot8]: <Screenshot 2025-05-09 at 10.30.17 PM.png>

Сам контейнер с nginx, его представление в tree:

![Screenshot][def screenshot9]

[def screenshot9]: <Screenshot 2025-05-09 at 10.19.43 PM.png>

Итоговый вариант основго compsoe.yaml:

![Screenshot][def screenshot10]

[def screenshot10]: <Screenshot 2025-05-09 at 10.34.55 PM.png>

Удалил один манифест. Появившаяся ошибка говорит о том, что есть контейнеры-сироты, они ранее создавались, через yaml, а он пропал. 
На скрине решаю эту проблему флагом --remove-orphans погасив проект целиком. 
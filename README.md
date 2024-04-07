# Test1lvlForPyDev

### Иструкция:

Галочка "Полное совпадение" означает, что будут собраны только полностью совпадающие ники, без учета регистара
Галочка "Учитывать регистр"означает, что будут собраны только полностью совпадающие ники, с учетом регистара

1) Введите ник
2) Нажать кнопку поиск
3) Ждите

Будет создана таблица Введенный_Ник.xlsx (Введенный_Ник это ник, в котом остались только буквы, цифры и пробелы,
поробелы заменены на "_"). Если таблица с таким именем уже существует, то она будет перезаписана

### Описание работы программы:

- интерфейс сделан с помощью flet
- запросы реализованы на aiohttp
- парсер с помощью bs4
- построчный эксторт в .xlsx с помощью openpyxl

для получения доступа к поиску по api steam необходимо чтобы значение sessionid в ссылке и в cookies совпали
sessionid получается в заголовках ответа от сайта "https://steamcommunity.com/"

### Немножко истории)

1) была быстрая версия парсера, но сбор данных был реализован через обычный список и потребление озу доходило до 12 гб
2) позже я ее переделал ее на работу с sql, т.к. необходим один исполняемый файл пришлось использовать sqlite, но в
   слетствии большого кол-ва запросов к бд sqlite пал
3) затем переделал на сохранение страниц, падало без причины после записа 10-15к файлов
4) в итоге результат по мере получения построчно записывается в .xlsx, но это работает относительно медленно
5) а после итога переписал обратно на обычный список, ато слишком медленно получилось
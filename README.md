# Homeworks
 Tasks
1) node_server
Создать веб сервер.

x-www-form-urlencoded запросы строками. Через Postman

API:

GET `/person` - возвращает данные о человеке

GET `/person/name` - возвращает только имя человека

GET `/person?name&age&surname` - возвращает данные полей, которые переданные в строке. Может быть name, age, surname, height, weight, degree, city, street, postCode

GET `/person/address` - возвращает только те поля, который относятся к адресу.

GET `/person/post/recipient` - возвращает только те поля, который необходимы для сформирования почтового отправления - имя, фамилия, город, улица, почтовый индекс

PUT `/person/update`, с телом {...anything} - запрос который перезаписывает в файле `/api/person.json` всем что было передано в теле.

2) Express_server_mock

Postman Post ->Body->Raw и например { "values": [2, 2, 2, 22, 1, 55, 2, 4, 33, 34, 555] }

x-www-form-urlencoded - передается строкой, а не объектом

Создать сервер Express, который будет накапливать запросы и выдавать их в виде некоторой статистики.

1) На сервер можно отправить данные POST /data/update, где body -> { values: [1, 2, 3....] }

2) Нужно отправить с Postman пару десятков запросов с разными body

3) Создать GET запрос /data/status-check, который вернёт структуру со следующей информацией: { count, valuesTotalLength, uniqueValues, ArithmeticMean }, где

count - количество загрузок данных

valuesTotalLength - длинна всех массивов вместе, которые были переданы

uniqueValues - массив уникальных значений из всех массивов, которые были переданы

ArithmeticMean - среднее арифметическое значений из всех массивов, которые были переданы

4) Каждый POST запрос должен создавать файл txt где будет хранится тело запроса в шифрованном AES виде (
https://cryptojs.gitbook.io/docs/#ciphers

).

5) Создать запрос GET /data/get, который вернет содержимое всех файлов в следующем виде:

{
"время создания файла 1": "содержимое файла в JSON",

"время создания файла 2": "содержимое файла в JSON",

"время создания файла 3": "содержимое файла в JSON",

"время создания файла 4": "содержимое файла в JSON",
}

3)TelegramBot&Server

Разработать два веб-сервиса:

Первый - BotApiWrapperService
Второй - BalancerService
Первый сервис реализует отправку данных в телеграмм бота.

Второй сервис получает запросы из Postman/любого другого веб приложения и пересылает их в первый сервис.

Каждый сервис - отдельное NodeJS приложение с express.js как фреймворком для веб сервера.

Реализовать:

1) Отправка прогноза температуры на 6 часов вперед в телеграм бота. Город - указан в get параметрах.

2) Отправка всей информации в текущий момент времени. Город также указан в get параметрах https://openweathermap.org/current

Endpoints на сервис BalancerService.

GET /weather/forecast/6h?city=London

GET /weather/current?city=London

1) https://tlgrm.ru/docs/bots#create-a-new-bot

2) https://github.com/yagop/node-telegram-bot-api


Важные коментарии:

1) Абсолютно все запросы должны идти на BalancerService, и только потом пересылаться на BotApiWrapperService, который в свою очередь пересылает на TelegramBot

2) Имя бота - произвольное, практически готовый пример реализации отправки текста - https://github.com/yagop/node-telegram-bot-api

3) Тут много хороших примеров - https://github.com/hosein2398/node-telegram-bot-api-tutorial

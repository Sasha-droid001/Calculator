Веб сервис для вычисления арифметических выражений

Описание
Этот проект реализует веб-сервис, который вычисляет арифметические выражения, переданные пользователем через HTTP-запрос.

Структура проекта


Запуск сервиса
1.Установите Go.
2.Склонируйте проект с GitHub:
git clone https://github.com/your-username/calc_service.git
3.Перейдите в папку проекта и запустите сервер:
go run ./cmd/calc_service/...
4.Сервис будет доступен по адресу: http://localhost:8080/api/v1/calculate.

Альтернативный запуск
Вы можете использовать скрипты для сборки и запуска:
Для Linux/MacOS:
./build/build.sh
Для Windows:
.\build\build.bat


Эндпоинты
POST /api/v1/calculate
Описание
Эндпоинт принимает JSON с математическим выражением.

Пример запроса с использованием PowerShell
Invoke-RestMethod -Uri "http://localhost:8080/api/v1/calculate" `
-Method POST `
-Headers @{"Content-Type"="application/json"} `
-Body '{"expression": "2+2*2"}'
Пример успешного ответа
json
Копировать код
{
  "result": "6.000000"
}
Пример ошибки 500
Если выражение содержит некорректный символ $, сервер вернёт ошибку 500:

Пример запроса
powershell
Копировать код
Invoke-RestMethod -Uri "http://localhost:8080/api/v1/calculate" `
-Method POST `
-Headers @{"Content-Type"="application/json"} `
-Body '{"expression": "1+$2"}'
Пример ответа
json
Копировать код
{
  "error": "Некорректное выражение"
}
Тестирование
Для запуска тестов выполните:

bash
Копировать код
go test ./...
Примечания
Для работы API требуется установленный Go (версии 1.18 и выше).
Все зависимости проекта управляются через go mod. Убедитесь, что в корне проекта находятся go.mod и go.sum.

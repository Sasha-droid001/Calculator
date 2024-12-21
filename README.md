# Простой веб-сервис для вычисления арифметических выражений

## Описание
Это проект веб-сервиса, который вычисляет арифметические выражения, переданные пользователем через HTTP-запрос.


## Запуск сервиса

1. Установите [Go](https://go.dev/dl/).
2. Склонируйте проект с GitHub:
    ```bash
    git clone https://github.com/Sasha-droid001/Calculator.git
    ```
3. Перейдите в папку проекта и запустите сервер:
    ```bash
    go run ./cmd/calc_service/...
    ```
4. Сервис будет доступен по адресу: [http://localhost/api/v1/calculate](http://localhost/api/v1/calculate).

## Эндпоинты

### `POST /api/v1/calculate`

#### Описание
Эндпоинт принимает JSON с математическим выражением POST запросом в теле.
Пример
{"expression": "2+2*2"}

#### Пример запроса с использованием PowerShell


```powershell
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


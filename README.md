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
    go run main.go
    ```
4. Сервис будет доступен по адресу: [http://localhost/api/v1/calculate](http://localhost/api/v1/calculate).

## Эндпоинты

### `POST /api/v1/calculate`

#### Описание
Эндпоинт принимает JSON с математическим выражением POST запросом в теле.
Пример
{"expression": "2+2*2"}

#### Пример запроса с использованием PowerShell



Пример корректного запроса к сервису
```powershell
Invoke-RestMethod -Uri "http://localhost:80/api/v1/calculate" `
>> -Method POST `
>> -Headers @{"Content-Type"="application/json"} `
>> -Body '{"expression": "2+2*2"}'
```
Пример успешного ответа json
код ответа: 200
{
  "result": "6"
}

Пример запроса с отсутствующим выражением
```powershell
Invoke-RestMethod -Uri "http://localhost/api/v1/calculate" `   
>> -Method POST `
>> -Headers @{"Content-Type"="application/json"} `
>> -Body '{"express": ""}' 
```       
Пример ответа json
код ответа: 422
{
  "error": "Expression is not valid"
}

Пример запроса с некорректным выражением
```powershell
Invoke-RestMethod -Uri "http://localhost/api/v1/calculate" `
>> -Method POST `
>> -Headers @{"Content-Type"="application/json"} `
>> -Body '{"expression": "2+2*/52"}'
```
Пример ответа json
код ответа: 422
{
  "error": "Expression is not valid"
}

Пример с пустым телом запроса
```powershell
Invoke-RestMethod -Uri "http://localhost/api/v1/calculate" `
>> -Method POST `
>> -Headers @{"Content-Type"="application/json"}
```
Пример ответа json
код ответа: 500
{
  "error": "Internal server error"
}

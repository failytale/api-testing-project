# API Bug-reports

## BUG-001: GET /api/companies не возвращает ошибку валидации при передаче limit=0

<table>
    <tr>
        <td colspan="2"><b>ID: </b>BUG-001</td>
    </tr>
    <tr>
        <td colspan="2"><b>Наименование: </b><code>GET /api/companies</code> не возвращает ошибку валидации при передаче <code>limit=0</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Описание: </b>при передаче query-параметра <code>limit=0</code> сервер возвращает успешный ответ <code>200 OK</code> и пустой массив <code>data</code>, хотя по спецификации API для параметра <code>limit</code> указано ограничение minimum: 1. Так как значение 0 не входит в допустимый диапазон, сервер должен вернуть ошибку валидации <code>422 Unprocessable Entity</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Severity:</b> Minor</td>
    </tr>
    <tr>
        <td colspan="2"><b>Priority:</b> Medium</td>
    </tr>
    <tr>
        <th rowspan="4">Окружение: </th>
        <td><b>Base URL: </b><code>https://restapi.tech</code></td>
    </tr>
    <tr>
        <td><b>API version: </b>0.1.0</td>
    </tr>
    <tr>
        <td><b>Tool: </b>Postman 12.15.8</td>
    </tr>
    <tr>
        <td><b>OS: </b>Windows 11 x64</td>
    </tr>
    <tr>
        <td colspan="2"><b>Связанный тест-кейс: </b><a href="#">CMP-LIST-008</a></td>
    </tr>
      <tr>
        <th rowspan="3">Шаги для воспроизведения:</th>
        <td>1. Выполнить запрос: <pre><code>curl --location 'https://restapi.tech/api/companies?limit=0'</code></pre></td>
    </tr>
    <tr>
        <td>2. Проверить статус-код</td>
    </tr>
    <tr>
        <td>3. Проверить тело ответа</td>
    </tr>
    <tr>
        <th>Ожидаемый результат</th>
        <th>Фактический результат</th>
    </tr>
    <tr>
        <td>1. Сервер возвращает статус-код: <code>422 Unprocessable Entity</code></td>
        <td>1. Сервер возвращает статус-код: <code>200 OK</code></td>
    </tr>
    <tr>
        <td>2. Тело ответа содержит информацию об ошибке валидации query-параметра <code>limit</code></td>
        <td>2. В теле ответа возвращается пустой массив <code>data</code>, а в объекте <code>meta</code> значение <code>limit</code> равно 0</td>
    </tr>
    <tr>
        <td><b>Пример ожидаемого ответа: </b><pre><code>{
    "detail": [
        {
            "loc": ["query", "limit"],
            "msg": "&lt;validation message&gt;",
            "type": "&lt;validation error type&gt;"
        }
    ]
}</code></pre></td>
        <td valign="top"><b>Пример фактического ответа: </b><pre><code>{ 
    "data": [], 
    "meta": { 
        "total": 7, 
        "limit": 0, 
        "offset": 0 
    } 
}</code></pre></td>
    </tr>
    <tr>
        <td colspan="2"><b>Вложения: </b><img width="100%" height="460" alt="1" src="https://github.com/user-attachments/assets/9165ec4e-3c1d-448c-8b38-2b546cb3a1eb" />
</td>
    </tr>
</table>    
              
## BUG-002: GET /api/companies возвращает все компании при передаче limit=-1 вместо ошибки валидации

<table>
    <tr>
        <td colspan="2"><b>ID: </b>BUG-002</td>
    </tr>
    <tr>
        <td colspan="2"><b>Наименование: </b><code>GET /api/companies</code> возвращает все компании при передаче <code>limit=-1</code> вместо ошибки валидации</td>
    </tr>
    <tr>
        <td colspan="2"><b>Описание:</b> при передаче query-параметра <code>limit=-1</code> сервер возвращает успешный ответ <code>200 OK</code> и список всех компаний, хотя по спецификации API для параметра <code>limit</code> указано ограничение minimum: 1. Так как отрицательное значение не входит в допустимый диапазон, сервер должен вернуть ошибку валидации <code>422 Unprocessable Entity</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Severity:</b> Major</td>
    </tr>
    <tr>
        <td colspan="2"><b>Priority:</b> Medium</td>
    </tr>
    <tr>
        <th rowspan="4">Окружение: </th>
        <td><b>Base URL: </b><code>https://restapi.tech</code></td>
    </tr>
    <tr>
        <td><b>API version: </b>0.1.0</td>
    </tr>
    <tr>
        <td><b>Tool: </b>Postman 12.15.8</td>
    </tr>
    <tr>
        <td><b>OS: </b>Windows 11 x64</td>
    </tr>
    <tr>
        <td colspan="2"><b>Связанный тест-кейс: </b><a href="#">CMP-LIST-009</a></td>
    </tr>
      <tr>
        <th rowspan="3">Шаги для воспроизведения:</th>
        <td>1. Выполнить запрос: <pre><code>curl --location 'https://restapi.tech/api/companies?limit=-1'</code></pre></td>
    </tr>
    <tr>
        <td>2. Проверить статус-код</td>
    </tr>
    <tr>
        <td>3. Проверить тело ответа</td>
    </tr>
    <tr>
        <th>Ожидаемый результат</th>
        <th>Фактический результат</th>
    </tr>
    <tr>
        <td>1. Сервер возвращает статус-код: <code>422 Unprocessable Entity</code></td>
        <td>1. Сервер возвращает статус-код: <code>200 OK</code></td>
    </tr>
    <tr>
        <td>2. Тело ответа содержит информацию об ошибке валидации query-параметра <code>limit</code></td>
        <td>2. В теле ответа возвращается список всех компаний, а в объекте <code>meta</code> значение <code>limit</code> равно -1</td>
    </tr>
    <tr>
        <td valign="top"><b>Пример ожидаемого ответа: </b><pre><code>{
    "detail": [
        {
            "loc": ["query", "limit"],
            "msg": "&lt;validation message&gt;",
            "type": "&lt;validation error type&gt;"
        }
    ]
}</code></pre></td>
        <td><b>Пример фактического ответа: </b><pre><code>{ 
    "data": [ 
        { 
            "company_id": 1, 
            "company_name": "Tesla", 
            "company_address": "Nicholastown, IL 80126",
            "company_status": "ACTIVE" 
        }, 
        { 
            "company_id": 2, 
            "company_name": "Google", 
            "company_address": "1093 Cooke Harbor Apt. 908",
            "company_status": "ACTIVE" 
        }, 
        { 
            "company_id": 3, 
            "company_name": "Toyota", 
            "company_address": "Davidberg, MN 88952", 
            "company_status": "ACTIVE" 
        } 
    ], 
    "meta": { 
        "total": 7, 
        "limit": -1, 
        "offset": 0 
    } 
}</code></pre></td>
    </tr>
    <tr>
        <td colspan="2"><b>Примечание: </b>фактический ответ сокращен для читаемости. В полном ответе сервер возвращает 7 компаний</td>
    </tr>
    <tr>
        <td colspan="2"><b>Вложения: </b><img width="100%" height="755" alt="2" src="https://github.com/user-attachments/assets/fc3af846-5c3b-49c0-927b-8001afc8002a" />
</td>
    </tr>
</table>    
              
## BUG-003: GET /api/users не возвращает ошибку валидации при передаче limit=0

<table>
    <tr>
        <td colspan="2"><b>ID: </b>BUG-003</td>
    </tr>
    <tr>
        <td colspan="2"><b>Наименование: </b><code>GET /api/users</code> не возвращает ошибку валидации при передаче <code>limit=0</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Описание: </b>при передаче query-параметра <code>limit=0</code> сервер возвращает успешный ответ <code>200 OK</code> и пустой массив <code>data</code>, хотя по спецификации API для параметра <code>limit</code> указано ограничение minimum: 1. Так как значение 0 не входит в допустимый диапазон, сервер должен вернуть ошибку валидации <code>422 Unprocessable Entity</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Severity:</b> Minor</td>
    </tr>
    <tr>
        <td colspan="2"><b>Priority:</b> Medium</td>
    </tr>
    <tr>
        <th rowspan="4">Окружение: </th>
        <td><b>Base URL: </b><code>https://restapi.tech</code></td>
    </tr>
    <tr>
        <td><b>API version: </b>0.1.0</td>
    </tr>
    <tr>
        <td><b>Tool: </b>Postman 12.15.8</td>
    </tr>
    <tr>
        <td><b>OS: </b>Windows 11 x64</td>
    </tr>
    <tr>
        <td colspan="2"><b>Связанный тест-кейс: </b><a href="#">USR-LIST-004</a></td>
    </tr>
      <tr>
        <th rowspan="3">Шаги для воспроизведения:</th>
        <td>1. Выполнить запрос: <pre><code>curl --location 'https://restapi.tech/api/users?limit=0'</code></pre></td>
    </tr>
    <tr>
        <td>2. Проверить статус-код</td>
    </tr>
    <tr>
        <td>3. Проверить тело ответа</td>
    </tr>
    <tr>
        <th>Ожидаемый результат</th>
        <th>Фактический результат</th>
    </tr>
    <tr>
        <td>1. Сервер возвращает статус-код: <code>422 Unprocessable Entity</code></td>
        <td>1. Сервер возвращает статус-код: <code>200 OK</code></td>
    </tr>
    <tr>
        <td>2. Тело ответа содержит информацию об ошибке валидации query-параметра <code>limit</code></td>
        <td>2. В теле ответа возвращается пустой массив <code>data</code>, а в объекте <code>meta</code> значение <code>limit</code> равно 0</td>
    </tr>
    <tr>
        <td><b>Пример ожидаемого ответа: </b><pre><code>{
    "detail": [
        {
            "loc": ["query", "limit"],
            "msg": "&lt;validation message&gt;",
            "type": "&lt;validation error type&gt;"
        }
    ]
}</code></pre></td>
        <td valign="top"><b>Пример фактического ответа: </b><pre><code>{ 
    "meta": { 
        "total": 33007, 
        "limit": 0, 
        "offset": 0 
    }, 
    "data": [] 
}</code></pre></td>
    </tr>
    <tr>
        <td colspan="2"><b>Вложения: </b><img width="100%" height="457" alt="3" src="https://github.com/user-attachments/assets/eedf4a2c-77f2-4c85-89f6-ca2657c69238" />
</td>
    </tr>
</table>    
              
## BUG-004: GET /api/users возвращает пользователей при передаче limit=-1 вместо ошибки валидации

<table>
    <tr>
        <td colspan="2"><b>ID: </b>BUG-004</td>
    </tr>
    <tr>
        <td colspan="2"><b>Наименование: </b><code>GET /api/users</code> возвращает пользователей при передаче <code>limit=-1</code> вместо ошибки валидации</td>
    </tr>
    <tr>
        <td colspan="2"><b>Описание: </b>при передаче query-параметра <code>limit=-1</code> сервер возвращает успешный ответ <code>200 OK</code> и список пользователей, хотя по спецификации API для параметра <code>limit</code> указано ограничение minimum: 1. Так как отрицательное значение не входит в допустимый диапазон, сервер должен вернуть ошибку валидации <code>422 Unprocessable Entity</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Severity:</b> Major</td>
    </tr>
    <tr>
        <td colspan="2"><b>Priority:</b> Medium</td>
    </tr>
    <tr>
        <th rowspan="4">Окружение: </th>
        <td><b>Base URL: </b><code>https://restapi.tech</code></td>
    </tr>
    <tr>
        <td><b>API version: </b>0.1.0</td>
    </tr>
    <tr>
        <td><b>Tool: </b>Postman 12.15.8</td>
    </tr>
    <tr>
        <td><b>OS: </b>Windows 11 x64</td>
    </tr>
    <tr>
        <td colspan="2"><b>Связанный тест-кейс: </b><a href="#">USR-LIST-005</a></td>
    </tr>
      <tr>
        <th rowspan="3">Шаги для воспроизведения:</th>
        <td>1. Выполнить запрос: <pre><code>curl --location 'https://restapi.tech/api/users?limit=-1'</code></pre></td>
    </tr>
    <tr>
        <td>2. Проверить статус-код</td>
    </tr>
    <tr>
        <td>3. Проверить тело ответа</td>
    </tr>
    <tr>
        <th>Ожидаемый результат</th>
        <th>Фактический результат</th>
    </tr>
    <tr>
        <td>1. Сервер возвращает статус-код: <code>422 Unprocessable Entity</code></td>
        <td>1. Сервер возвращает статус-код: <code>200 OK</code></td>
    </tr>
    <tr>
        <td>2. Тело ответа содержит информацию об ошибке валидации query-параметра <code>limit</code></td>
        <td>2. В теле ответа возвращается список всех пользователей, а в объекте <code>meta</code> значение <code>limit</code> равно -1</td>
    </tr>
    <tr>
        <td valign="top"><b>Пример ожидаемого ответа: </b><pre><code>{
    "detail": [
        {
            "loc": ["query", "limit"],
            "msg": "&lt;validation message&gt;",
            "type": "&lt;validation error type&gt;"
        }
    ]
}</code></pre></td>
        <td><b>Пример фактического ответа: </b><pre><code>{ 
    "meta": { 
        "total": 33007, 
        "limit": -1, 
        "offset": 0 
    }, 
    "data": [ 
        { 
            "first_name": "Bred", 
            "last_name": "Pit", 
            "company_id": 3, 
            "user_id": 166 
        }, 
        { 
            "first_name": "string", 
            "last_name": "string", 
            "company_id": 3, 
            "user_id": 210 
        }, 
        { 
            "first_name": "Petr", 
            "last_name": "Pavel", 
            "company_id": 1, 
            "user_id": 263 
        } 
    ] 
}
</code></pre></td>
    </tr>
    <tr>
        <td colspan="2"><b>Примечание: </b>фактический ответ сокращен для читаемости. В полном ответе сервер возвращает список всех пользователей</td>
    </tr>
    <tr>
        <td colspan="2"><b>Вложения: </b><img width="100%" height="755" alt="4" src="https://github.com/user-attachments/assets/6a4a38e0-5be9-4eb1-9643-781d4d1052c1" />
</td>
    </tr>
</table>

## BUG-005: DELETE /api/users/{user_id} возвращает null вместо JSON-объекта

<table>
    <tr>
        <td colspan="2"><b>ID: </b>BUG-005</td>
    </tr>
    <tr>
        <td colspan="2"><b>Наименование: </b><code>DELETE /api/users/{user_id}</code> возвращает <code>null</code> вместо JSON-объекта</td>
    </tr>
    <tr>
        <td colspan="2"><b>Описание: </b>после успешного удаления существующего пользователя сервер возвращает статус-код <code>202 Accepted</code>, но тело ответа содержит значение <code>null</code>. Согласно ожидаемому контракту успешного DELETE-запроса, тело ответа должно быть JSON-объектом и не должно быть равно <code>null</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Severity:</b> Minor</td>
    </tr>
    <tr>
        <td colspan="2"><b>Priority:</b> Medium</td>
    </tr>
    <tr>
        <th rowspan="4">Окружение: </th>
        <td><b>Base URL: </b><code>https://restapi.tech</code></td>
    </tr>
    <tr>
        <td><b>API version: </b>0.1.0</td>
    </tr>
    <tr>
        <td><b>Tool: </b>Postman 12.15.8</td>
    </tr>
    <tr>
        <td><b>OS: </b>Windows 11 x64</td>
    </tr>
    <tr>
        <td colspan="2"><b>Связанные тест-кейс: </b><a href="#">USR-DEL-001</a></td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>создать тестового пользователя с привязкой к активной компании и сохранить полученный <code>user_id</code> как <code>{{createdUserId}}</code>. Запрос для создания пользователя: <pre><code>curl --location 'https://restapi.tech/api/users' \
--header 'Content-Type: application/json' \
--data '{
  "first_name": "User",
  "last_name": "Test",
  "company_id": 1
}'</code></pre></td>
    </tr>
      <tr>
        <th rowspan="3">Шаги для воспроизведения:</th>
        <td>1. Выполнить запрос для созданного пользователя: <pre><code>curl --location --globoff --request DELETE '{{baseUrl}}/api/users/{{createdUserId}}'</code></pre></td>
    </tr>
    <tr>
        <td>2. Проверить статус-код</td>
    </tr>
    <tr>
        <td>3. Проверить тело ответа</td>
    </tr>
    <tr>
        <th>Ожидаемый результат</th>
        <th>Фактический результат</th>
    </tr>
    <tr>
        <td>1. Сервер возвращает статус-код: <code>202 Accepted</code></td>
        <td>1. Сервер возвращает статус-код: <code>202 Accepted</code></td>
    </tr>
    <tr>
        <td>2. Тело ответа является JSON-объектом и не равно <code>null</code></td>
        <td>2. Тело ответа содержит значение <code>null</code></td>
    </tr>
    <tr>
        <td nowrap><b>Пример ожидаемого ответа: </b><pre><code>{}</code></pre></td>
        <td><b>Пример фактического ответа: </b><pre><code>null</code></pre></td>
    </tr>
    <tr>
        <td colspan="2"><b>Вложения: </b><img width="100%" height="432" alt="5" src="https://github.com/user-attachments/assets/eac78082-7e92-449f-a138-2517603707da" />
</td>
    </tr>
</table>

## BUG-006: GET /api/issues/companies игнорирует значение query-параметра status

<table>
    <tr>
        <td colspan="2"><b>ID: </b>BUG-006</td>
    </tr>
    <tr>
        <td colspan="2"><b>Наименование: </b><code>GET /api/issues/companies</code> игнорирует значение query-параметра <code>status</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Описание: </b>при передаче разных значений query-параметра <code>status</code> сервер возвращает одинаковый набор компаний со статусом <code>CLOSED</code>. Значение параметра фильтрации не влияет на результат ответа</td>
    </tr>
    <tr>
        <td colspan="2"><b>Severity:</b> Major</td>
    </tr>
    <tr>
        <td colspan="2"><b>Priority:</b> Medium</td>
    </tr>
    <tr>
        <th rowspan="4">Окружение: </th>
        <td><b>Base URL: </b><code>https://restapi.tech</code></td>
    </tr>
    <tr>
        <td><b>API version: </b>0.1.0</td>
    </tr>
    <tr>
        <td><b>Tool: </b>Postman 12.15.8</td>
    </tr>
    <tr>
        <td><b>OS: </b>Windows 11 x64</td>
    </tr>
    <tr>
        <th rowspan="4">Шаги для воспроизведения:</th>
        <td>1. Выполнить запрос с параметром <code>status=ACTIVE</code>: <pre><code>curl --location 'https://restapi.tech/api/issues/companies?status=ACTIVE'</code></pre></td>
    </tr>
    <tr>
        <td>2. Проверить статус-код и значения поля <code>company_status</code> в массиве <code>data</code></td>
    </tr>
    <tr>
        <td>3. Выполнить запрос с параметром <code>status=BANKRUPT</code>: <pre><code>curl --location 'https://restapi.tech/api/issues/companies?status=BANKRUPT'</td>
    </tr>
    <tr>
        <td>4. Проверить статус-код и значения поля <code>company_status</code> в массиве <code>data</code></td>
    </tr>
    <tr>
        <th>Ожидаемый результат</th>
        <th>Фактический результат</th>
    </tr>
    <tr>
        <td>1. При запросе <code>status=ACTIVE</code> сервер возвращает статус-код <code>200 OK</code></td>
        <td>1. При запросе <code>status=ACTIVE</code> сервер возвращает статус-код <code>200 OK</code></td>
    </tr>
    <tr>
        <td>2. Все объекты в массиве <code>data</code> имеют значение <code>"company_status": "ACTIVE"</code></td>
        <td>2. В массиве <code>data</code> возвращаются компании со статусом <code>CLOSED</code></td>
    </tr>
    <tr>
        <td>3. При запросе <code>status=BANKRUPT</code> сервер возвращает статус-код <code>200 OK</code></td>
        <td>3. При запросе <code>status=BANKRUPT</code> сервер возвращает статус-код <code>200 OK</code></td>
    </tr>
    <tr>
        <td>4. Все объекты в массиве <code>data</code> имеют значение <code>"company_status": "BANKRUPT"</code></td>
        <td>4. В массиве <code>data</code> возвращаются компании со статусом <code>CLOSED</code></td>
    </tr>
    <tr>
        <td valign="top" colspan="2"><b>Пример фактического ответа для обоих запросов: </b><pre><code>{
  "data": [
    {
      "company_id": 5,
      "company_name": "Apple",
      "company_address": "Patrickchester, FL 93690",
      "company_status": "CLOSED"
    },
    {
      "company_id": 6,
      "company_name": "BitcoinCorp",
      "company_address": "85958 Cindy Wall",
      "company_status": "CLOSED"
    }
  ],
  "meta": {
    "total": 7,
    "limit": 3,
    "offset": 0
  }
}</code></pre></td>
    </tr>
    <tr>
        <td colspan="2"><b>Вложения: </b><img width="100%" height="741" alt="6" src="https://github.com/user-attachments/assets/f3deb74f-f47a-4859-82e9-bddc56c92792" />
</td>
    </tr>
</table>

## BUG-007: Время ответа GET /api/issues/companies/{company_id} превышает допустимое значение

<table>
    <tr>
        <td colspan="2"><b>ID: </b>BUG-007</td>
    </tr>
    <tr>
        <td colspan="2"><b>Наименование: </b>Время ответа <code>GET /api/issues/companies/{company_id}</code> превышает допустимое значение</td>
    </tr>
    <tr>
        <td colspan="2"><b>Описание: </b>при запросе информации о компании по <code>company_id</code> время ответа сервера составляет около 5 секунд, что значительно превышает установленное ограничение производительности ≤ 500 ms</td>
    </tr>
    <tr>
        <td colspan="2"><b>Severity:</b> Major</td>
    </tr>
    <tr>
        <td colspan="2"><b>Priority:</b> Medium</td>
    </tr>
    <tr>
        <th rowspan="4">Окружение: </th>
        <td><b>Base URL: </b><code>https://restapi.tech</code></td>
    </tr>
    <tr>
        <td><b>API version: </b>0.1.0</td>
    </tr>
    <tr>
        <td><b>Tool: </b>Postman 12.15.8</td>
    </tr>
    <tr>
        <td><b>OS: </b>Windows 11 x64</td>
    </tr>
      <tr>
        <th rowspan="3">Шаги для воспроизведения:</th>
        <td>1. Выполнить запрос: <pre><code>curl --location 'https://restapi.tech/api/issues/companies/4' \
--header 'Accept-Language: EN'</code></pre></td>
    </tr>
    <tr>
        <td>2. Проверить статус-код</td>
    </tr>
    <tr>
        <td>3. Проверить время ответа сервера</td>
    </tr>
    <tr>
        <th>Ожидаемый результат</th>
        <th>Фактический результат</th>
    </tr>
    <tr>
        <td>1. Сервер возвращает статус-код: <code>200 OK</code></td>
        <td>1. Сервер возвращает статус-код: <code>200 OK</code></td>
    </tr>
    <tr>
        <td nowrap>2. Время ответа сервера не превышает 500 ms</td>
        <td>2. Время ответа сервера составляет около 5000 ms.</td>
    </tr>
    <tr>
        <td colspan="2"><b>Вложения: </b><img width="100%" height="477" alt="7" src="https://github.com/user-attachments/assets/3ff1800a-4ab0-4d6a-a5ab-bfb53c9e32c1" /></td>
    </tr>
</table>

## BUG-008: GET /api/issues/users/{user_id} возвращает 202 Accepted вместо 200 OK

<table>
    <tr>
        <td colspan="2"><b>ID: </b>BUG-008</td>
    </tr>
    <tr>
        <td colspan="2"><b>Наименование: </b><code>GET /api/issues/users/{user_id}</code> возвращает <code>202 Accepted</code> вместо <code>200 OK</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Описание: </b>при успешном получении информации о пользователе сервер возвращает статус-код <code>202 Accepted</code>, хотя для успешного GET-запроса спецификация API предусматривает статус-код <code>200 OK</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Severity:</b> Minor</td>
    </tr>
    <tr>
        <td colspan="2"><b>Priority:</b> Medium</td>
    </tr>
    <tr>
        <th rowspan="4">Окружение: </th>
        <td><b>Base URL: </b><code>https://restapi.tech</code></td>
    </tr>
    <tr>
        <td><b>API version: </b>0.1.0</td>
    </tr>
    <tr>
        <td><b>Tool: </b>Postman 12.15.8</td>
    </tr>
    <tr>
        <td><b>OS: </b>Windows 11 x64</td>
    </tr>
      <tr>
        <th rowspan="2">Шаги для воспроизведения:</th>
        <td>1. Выполнить запрос: <pre><code>curl --location 'https://restapi.tech/api/issues/users/210'</code></pre></td>
    </tr>
    <tr>
        <td>2. Проверить статус-код</td>
    </tr>
    <tr>
        <th>Ожидаемый результат</th>
        <th>Фактический результат</th>
    </tr>
    <tr>
        <td>1. Сервер возвращает статус-код: <code>200 OK</code></td>
        <td>1. Сервер возвращает статус-код: <code>202 Accepted</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Вложения: </b><img width="100%" height="365" alt="8-9" src="https://github.com/user-attachments/assets/7e0fc9a3-3dca-498e-8eed-6b267358ba41" />
</td>
    </tr>
</table>

## BUG-009: Ответ GET /api/issues/users/{user_id} не содержит обязательное поле user_id

<table>
    <tr>
        <td colspan="2"><b>ID: </b>BUG-009</td>
    </tr>
    <tr>
        <td colspan="2"><b>Наименование: </b>Ответ <code>GET /api/issues/users/{user_id}</code> не содержит обязательное поле <code>user_id</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Описание: </b>при запросе информации о пользователе сервер возвращает тело ответа без обязательного поля <code>user_id</code>. Согласно контракту API, успешный ответ должен соответствовать схеме пользователя</td>
    </tr>
    <tr>
        <td colspan="2"><b>Severity:</b> Major</td>
    </tr>
    <tr>
        <td colspan="2"><b>Priority:</b> Medium</td>
    </tr>
    <tr>
        <th rowspan="4">Окружение: </th>
        <td><b>Base URL: </b><code>https://restapi.tech</code></td>
    </tr>
    <tr>
        <td><b>API version: </b>0.1.0</td>
    </tr>
    <tr>
        <td><b>Tool: </b>Postman 12.15.8</td>
    </tr>
    <tr>
        <td><b>OS: </b>Windows 11 x64</td>
    </tr>
      <tr>
        <th rowspan="2">Шаги для воспроизведения:</th>
        <td>1. Выполнить запрос: <pre><code>curl --location 'https://restapi.tech/api/issues/users/210'</code></pre></td>
    </tr>
    <tr>
        <td>2. Проверить тело ответа</td>
    </tr>
    <tr>
        <th>Ожидаемый результат</th>
        <th>Фактический результат</th>
    </tr>
    <tr>
        <td nowrap>1. Тело ответа содержит обязательное поле <code>user_id</code></td>
        <td>1. В теле ответа отсутствует обязательное поле <code>user_id</code></td>
    </tr>
    <tr>
        <td valign="top"><b>Пример ожидаемого ответа: </b><pre><code>{
  "first_name": "string",
  "last_name": "string",
  "company_id": null,
  "user_id": 210
}</code></pre></td>
        <td valign="top"><b>Пример фактического ответа: </b><pre><code>{
  "first_name": "string",
  "last_name": "string"
}
</code></pre></td>
    </tr>
    <tr>
        <td colspan="2"><b>Вложения: </b><img width="100%" height="365" alt="8-9" src="https://github.com/user-attachments/assets/8aa73d2d-3317-4ac0-917b-d1020fa837e7" />
</td>
    </tr>
</table>

## BUG-010: GET /api/issues/users/{user_id} возвращает 500 Internal Server Error для пользователя с null в полях

<table>
    <tr>
        <td colspan="2"><b>ID: </b>BUG-010</td>
    </tr>
    <tr>
        <td colspan="2"><b>Наименование: </b><code>GET /api/issues/users/{user_id}</code> возвращает <code>500 Internal Server Error</code> для пользователя с <code>null</code> в полях</td>
    </tr>
    <tr>
        <td colspan="2"><b>Описание: </b>при запросе информации о пользователе, у которого поля <code>first_name</code> и/или <code>company_id</code> имеют значение <code>null</code>, сервер возвращает ошибку <code>500 Internal Server Error</code>. Согласно схеме ответа, поля <code>first_name</code> и <code>company_id</code> являются <code>nullable</code> по контракту API, поэтому сервер должен корректно обработать такие данные и вернуть успешный ответ с информацией о пользователе</td>
    </tr>
    <tr>
        <td colspan="2"><b>Severity:</b> Major</td>
    </tr>
    <tr>
        <td colspan="2"><b>Priority:</b> High</td>
    </tr>
    <tr>
        <th rowspan="4">Окружение: </th>
        <td><b>Base URL: </b><code>https://restapi.tech</code></td>
    </tr>
    <tr>
        <td><b>API version: </b>0.1.0</td>
    </tr>
    <tr>
        <td><b>Tool: </b>Postman 12.15.8</td>
    </tr>
    <tr>
        <td><b>OS: </b>Windows 11 x64</td>
    </tr>
      <tr>
        <th rowspan="3">Шаги для воспроизведения:</th>
        <td>1. Выполнить запрос: <pre><code>curl --location 'https://restapi.tech/api/issues/users/286'</code></pre></td>
    </tr>
    <tr>
        <td>2. Проверить статус-код</td>
    </tr>
    <tr>
        <td>3. Проверить тело ответа</td>
    </tr>
    <tr>
        <th>Ожидаемый результат</th>
        <th>Фактический результат</th>
    </tr>
    <tr>
        <td>1. Сервер возвращает статус-код: <code>200 OK</code></td>
        <td>1. Сервер возвращает статус-код: <code>500 Internal Server Error</code></td>
    </tr>
    <tr>
        <td>2. Тело ответа соответствует схеме пользователя</td>
        <td>2. Тело ответа содержит текст ошибки <code>Internal Server Error</code></td>
    </tr>
    <tr>
        <td>3. Поля <code>first_name</code> и <code>company_id</code> корректно возвращаются со значением <code>null</code></td>
        <td>3. Информация о пользователе не возвращается</td>
    </tr>
    <tr>
        <td><b>Пример ожидаемого ответа: </b><pre><code>{
  "first_name": null,
  "last_name": "Samosskiy",
  "company_id": null,
  "user_id": 286
}</code></pre></td>
        <td valign="top"><b>Пример фактического ответа: </b><pre><code>Internal Server Error</code></pre></td>
    </tr>
    <tr>
        <td colspan="2"><b>Вложения: </b><img width="100%" height="300" alt="10" src="https://github.com/user-attachments/assets/fd52961a-71f9-4472-b9a8-6cebbcef1d17" />
</td>
    </tr>
</table>

## BUG-011: POST /api/issues/users возвращает значения полей, отличающиеся от переданных в запросе

<table>
    <tr>
        <td colspan="2"><b>ID: </b>BUG-011</td>
    </tr>
    <tr>
        <td colspan="2"><b>Наименование: </b><code>POST /api/issues/users</code> возвращает значения полей, отличающиеся от переданных в запросе</td>
    </tr>
    <tr>
        <td colspan="2"><b>Описание: </b>при создании пользователя сервер возвращает успешный ответ, но значения полей <code>first_name</code> и <code>last_name</code> в теле ответа не совпадают со значениями, переданными в теле запроса</td>
    </tr>
    <tr>
        <td colspan="2"><b>Severity:</b> Major</td>
    </tr>
    <tr>
        <td colspan="2"><b>Priority:</b> High</td>
    </tr>
    <tr>
        <th rowspan="4">Окружение: </th>
        <td><b>Base URL: </b><code>https://restapi.tech</code></td>
    </tr>
    <tr>
        <td><b>API version: </b>0.1.0</td>
    </tr>
    <tr>
        <td><b>Tool: </b>Postman 12.15.8</td>
    </tr>
    <tr>
        <td><b>OS: </b>Windows 11 x64</td>
    </tr>
      <tr>
        <th rowspan="3">Шаги для воспроизведения:</th>
        <td>1. Выполнить запрос: <pre><code>curl --location 'https://restapi.tech/api/issues/users' \
--header 'Content-Type: application/json' \
--data '{
  "first_name": "Tyler",
  "last_name": "Durden",
  "company_id": 3
}'</code></pre></td>
    </tr>
    <tr>
        <td>2. Проверить статус-код</td>
    </tr>
    <tr>
        <td>3. Проверить тело ответа</td>
    </tr>
    <tr>
        <th>Ожидаемый результат</th>
        <th>Фактический результат</th>
    </tr>
    <tr>
        <td>1. Сервер возвращает статус-код: <code>201 Created</code></td>
        <td>1. Сервер возвращает статус-код: <code>201 Created</code></td>
    </tr>
    <tr>
        <td>2. Значение поля <code>first_name</code> в ответе равно <code>Tyler</code></td>
        <td>2. Значение поля <code>first_name</code> в ответе равно <code>Ne ny eto odnoznachno</code></td>
    </tr>
    <tr>
        <td>3. Значение поля <code>last_name</code> в ответе равно <code>Durden</code></td>
        <td>3. Значение поля <code>last_name</code> в ответе равно <code>BAGGGGGGGG</code></td>
    </tr>
    <tr>
        <td>4. Значение поля <code>company_id</code> в ответе равно <code>3</code></td>
        <td>4. Значение поля <code>company_id</code> в ответе равно <code>3</code></td>
    </tr>
    <tr>
        <td>5. Поле <code>user_id</code> присутствует в ответе и содержит целое положительное число, сгенерированное сервером</td>
        <td>5. Поле <code>user_id</code> присутствует в ответе и содержит значение <code>45198</code>, сгенерированное сервером</td>
    </tr>
    <tr>
        <td><b>Пример ожидаемого ответа: </b><pre><code>{
  "first_name": "Tyler",
  "last_name": "Durden",
  "company_id": 3,
  "user_id": &lt;generated_user_id&gt;
}</code></pre></td>
        <td valign="top"><b>Пример фактического ответа: </b><pre><code>{
  "first_name": "Ne ny eto odnoznachno",
  "last_name": "BAGGGGGGGG",
  "company_id": 3,
  "user_id": 45198
}</code></pre></td>
    </tr>
    <tr>
        <td colspan="2"><b>Вложения: </b><img width="100%" height="407" alt="11" src="https://github.com/user-attachments/assets/2b7ae0c8-5d4b-44aa-a79a-f409497cf2a8" />
</td>
    </tr>
</table>

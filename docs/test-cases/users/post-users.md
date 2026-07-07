# Test Cases — POST /api/users

## USR-POST-001: Создание пользователя с валидными значениями всех полей

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-POST-001</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Создание пользователя с валидными значениями всех полей</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>High</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>В базе данных существует активная компания с <code>company_id = {{activeCompanyId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Постусловие: </b>Отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><pre><code>{
  "first_name": "Tyler",
  "last_name": "Durden",
  "company_id": {{activeCompanyId}}
}</code></pre></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить POST-запрос на <code>{{baseUrl}}/api/users</code> с телом запроса</td>
        <td>Статус-код: <code>201 Created</code></td>
    </tr>
    <tr>
        <td>2. Сохранить <code>user_id</code> из тела ответа как <code>{{createdUserId}}</code></td>
        <td>Значение <code>user_id</code> сохранено как <code>{{createdUserId}}</code></td>
    </tr>
    <tr>
        <td>3. Проверить время ответа сервера</td>
        <td>Время ответа сервера ≤ 500 ms</td>
    </tr>
    <tr>
        <td>4. Проверить заголовки ответа</td>
        <td><code>Content-Type: application/json</code></td>
    </tr>
    <tr>
        <td>5. Проверить структуру ответа (Schema Validation)</td>
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#responseuser">ResponseUser</a></td>
    </tr>
    <tr>
        <td>6. Проверить значения полей ответа</td>
        <td>- <code>first_name: Tyler</code>,<br>
        - <code>last_name: Durden</code>,<br>
        - <code>company_id: {{activeCompanyId}}</code>,<br>
        - <code>user_id > 0</code>, сгенерировано сервером и является целым числом</td>
    </tr>
</table>

## USR-POST-002: Создание пользователя со значением first_name = null

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-POST-002</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Создание пользователя со значением <code>first_name = null</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>High</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>В базе данных существует активная компания с <code>company_id = {{activeCompanyId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Постусловие: </b>Отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><pre><code>{
  "first_name": null,
  "last_name": "Durden",
  "company_id": {{activeCompanyId}}
}</code></pre></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить POST-запрос на <code>{{baseUrl}}/api/users</code> с телом запроса</td>
        <td>Статус-код: <code>201 Created</code></td>
    </tr>
    <tr>
        <td>2. Сохранить <code>user_id</code> из тела ответа как <code>{{createdUserId}}</code></td>
        <td>Значение <code>user_id</code> сохранено как <code>{{createdUserId}}</code></td>
    </tr>
    <tr>
        <td>3. Проверить время ответа сервера</td>
        <td>Время ответа сервера ≤ 500 ms</td>
    </tr>
    <tr>
        <td>4. Проверить заголовки ответа</td>
        <td><code>Content-Type: application/json</code></td>
    </tr>
    <tr>
        <td>5. Проверить структуру ответа (Schema Validation)</td>
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#responseuser">ResponseUser</a></td>
    </tr>
    <tr>
        <td>6. Проверить значения полей ответа</td>
        <td>- <code>first_name: null</code>,<br>
        - <code>last_name: Durden</code>,<br>
        - <code>company_id: {{activeCompanyId}}</code>,<br>
        - <code>user_id > 0</code>, сгенерировано сервером и является целым числом</td>
    </tr>
</table>

## USR-POST-003: Проверка обработки значения last_name = null при создании пользователя

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-POST-003</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки значения <code>last_name = null</code> при создании пользователя</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>High</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>В базе данных существует активная компания с <code>company_id = {{activeCompanyId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><pre><code>{
  "first_name": "Tyler",
  "last_name": null,
  "company_id": {{activeCompanyId}}
}</code></pre></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить POST-запрос на <code>{{baseUrl}}/api/users</code> с телом запроса</td>
        <td>Статус-код: <code>422 Unprocessable Entity</code></td>
    </tr>
    <tr>
        <td>2. Проверить время ответа сервера</td>
        <td>Время ответа сервера ≤ 500 ms</td>
    </tr>
    <tr>
        <td>3. Проверить заголовки ответа</td>
        <td><code>Content-Type: application/json</code></td>
    </tr>
    <tr>
        <td>4. Проверить структуру ответа (Schema Validation)</td>
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#httpvalidationerror">HTTPValidationError</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>В массиве <code>detail</code> объект содержит: <br>
        - <code>loc: [body, last_name]</code>, <br>
        - <code>msg: Input should be a valid string</code>, <br>
        - <code>type: string_type</code></td>
    </tr>
</table>

## USR-POST-004: Создание пользователя со значением company_id = null

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-POST-004</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Создание пользователя со значением <code>company_id = null</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>High</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Постусловие: </b>Отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><pre><code>{
  "first_name": "Tyler",
  "last_name": "Durden",
  "company_id": null
}</code></pre></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить POST-запрос на <code>{{baseUrl}}/api/users</code> с телом запроса</td>
        <td>Статус-код: <code>201 Created</code></td>
    </tr>
    <tr>
        <td>2. Сохранить <code>user_id</code> из тела ответа как <code>{{createdUserId}}</code></td>
        <td>Значение <code>user_id</code> сохранено как <code>{{createdUserId}}</code></td>
    </tr>
    <tr>
        <td>3. Проверить время ответа сервера</td>
        <td>Время ответа сервера ≤ 500 ms</td>
    </tr>
    <tr>
        <td>4. Проверить заголовки ответа</td>
        <td><code>Content-Type: application/json</code></td>
    </tr>
    <tr>
        <td>5. Проверить структуру ответа (Schema Validation)</td>
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#responseuser">ResponseUser</a></td>
    </tr>
    <tr>
        <td>6. Проверить значения полей ответа</td>
        <td>- <code>first_name: Tyler</code>,<br>
        - <code>last_name: Durden</code>,<br>
        - <code>company_id: null</code>,<br>
        - <code>user_id > 0</code>, сгенерировано сервером и является целым числом</td>
    </tr>
</table>

## USR-POST-005: Проверка обработки запроса без обязательного поля last_name при создании пользователя

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-POST-005</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки запроса без обязательного поля <code>last_name</code> при создании пользователя</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>High</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>В базе данных существует активная компания с <code>company_id = {{activeCompanyId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><pre><code>{
  "first_name": "Tyler",
  "company_id": {{activeCompanyId}}
}</code></pre></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить POST-запрос на <code>{{baseUrl}}/api/users</code> с телом запроса</td>
        <td>Статус-код: <code>422 Unprocessable Entity</code></td>
    </tr>
    <tr>
        <td>2. Проверить время ответа сервера</td>
        <td>Время ответа сервера ≤ 500 ms</td>
    </tr>
    <tr>
        <td>3. Проверить заголовки ответа</td>
        <td><code>Content-Type: application/json</code></td>
    </tr>
    <tr>
        <td>4. Проверить структуру ответа (Schema Validation)</td>
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#httpvalidationerror">HTTPValidationError</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>В массиве <code>detail</code> объект содержит: <br>
        - <code>loc: [body, last_name]</code>, <br>
        - <code>msg: Field required</code>, <br>
        - <code>type: missing</code></td>
    </tr>
</table>

## USR-POST-006: Проверка обработки попытки создания пользователя с привязкой к компании со статусом "CLOSED"

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-POST-006</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки попытки создания пользователя с привязкой к компании со статусом <code>CLOSED</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>High</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>В базе данных существует закрытая компания с <code>company_id = {{closedCompanyId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><pre><code>{
  "first_name": "Tyler",
  "last_name": "Durden",
  "company_id": {{closedCompanyId}}
}</code></pre></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить POST-запрос на <code>{{baseUrl}}/api/users</code> с телом запроса</td>
        <td>Статус-код: <code>400 Bad Request</code></td>
    </tr>
    <tr>
        <td>2. Проверить время ответа сервера</td>
        <td>Время ответа сервера ≤ 500 ms</td>
    </tr>
    <tr>
        <td>3. Проверить заголовки ответа</td>
        <td><code>Content-Type: application/json</code></td>
    </tr>
    <tr>
        <td>4. Проверить структуру ответа (Schema Validation)</td>
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#errordetail">ErrorDetail</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>Объект <code>detail</code> содержит:<br>
        - <code>reason: You can only register with companies with ACTIVE status</code></td>
    </tr>
</table>

## USR-POST-007: Проверка обработки попытки создания пользователя с привязкой к компании со статусом "BANKRUPT"

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-POST-007</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки попытки создания пользователя с привязкой к компании со статусом <code>BANKRUPT</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>High</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>В базе данных существует закрытая компания с <code>company_id = {{bankruptCompanyId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><pre><code>{
  "first_name": "Tyler",
  "last_name": "Durden",
  "company_id": {{bankruptCompanyId}}
}</code></pre></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить POST-запрос на <code>{{baseUrl}}/api/users</code> с телом запроса</td>
        <td>Статус-код: <code>400 Bad Request</code></td>
    </tr>
    <tr>
        <td>2. Проверить время ответа сервера</td>
        <td>Время ответа сервера ≤ 500 ms</td>
    </tr>
    <tr>
        <td>3. Проверить заголовки ответа</td>
        <td><code>Content-Type: application/json</code></td>
    </tr>
    <tr>
        <td>4. Проверить структуру ответа (Schema Validation)</td>
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#errordetail">ErrorDetail</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>Объект <code>detail</code> содержит:<br>
        - <code>reason: You can only register with companies with ACTIVE status</code></td>
    </tr>
</table>

## USR-POST-008: Проверка обработки несуществующего значения поля company_id при создании пользователя

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-POST-008</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки несуществующего значения поля <code>company_id</code> при создании пользователя</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>High</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>В базе данных отсутствует компания с <code>company_id = {{nonexistentCompanyId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><pre><code>{
  "first_name": "Tyler",
  "last_name": "Durden",
  "company_id": {{nonexistentCompanyId}}
}</code></pre></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить POST-запрос на <code>{{baseUrl}}/api/users</code> с телом запроса</td>
        <td>Статус-код: <code>404 Not Found</code></td>
    </tr>
    <tr>
        <td>2. Проверить время ответа сервера</td>
        <td>Время ответа сервера ≤ 500 ms</td>
    </tr>
    <tr>
        <td>3. Проверить заголовки ответа</td>
        <td><code>Content-Type: application/json</code></td>
    </tr>
    <tr>
        <td>4. Проверить структуру ответа (Schema Validation)</td>
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#errordetail">ErrorDetail</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>Объект <code>detail</code> содержит:<br>
        - <code>reason: Company with requested id: &lt;nonexistentCompanyId&gt; is absent</code></td>
    </tr>
</table>

## USR-POST-009: Проверка обработки попытки создания пользователя без тела запроса

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-POST-009</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки попытки создания пользователя без тела запроса</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>High</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить POST-запрос на <code>{{baseUrl}}/api/users</code> без тела запроса</td>
        <td>Статус-код: <code>422 Unprocessable Entity</code></td>
    </tr>
    <tr>
        <td>2. Проверить время ответа сервера</td>
        <td>Время ответа сервера ≤ 500 ms</td>
    </tr>
    <tr>
        <td>3. Проверить заголовки ответа</td>
        <td><code>Content-Type: application/json</code></td>
    </tr>
    <tr>
        <td>4. Проверить структуру ответа (Schema Validation)</td>
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#httpvalidationerror">HTTPValidationError</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>В массиве <code>detail</code> объект содержит: <br>
        - <code>loc: [body]</code>, <br>
        - <code>msg: Field required</code>, <br>
        - <code>type: missing</code></td>
    </tr>
</table>

## USR-POST-010: Создание двух пользователей с идентичными данными

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-POST-010</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Создание двух пользователей с идентичными данными</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>В базе данных существует активная компания с <code>company_id = {{activeCompanyId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Постусловие: </b>
        <ol>
            <li>Отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{{createdUserId1}}</code></li>
            <li>Отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{{createdUserId2}}</code></li>
        </ol>
        </td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><pre><code>{
  "first_name": "Marla",
  "last_name": "Singer",
  "company_id": {{activeCompanyId}}
}</code></pre></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить POST-запрос на <code>{{baseUrl}}/api/users</code> с телом запроса</td>
        <td>Статус-код: <code>201 Created</code><br>Тело ответа сохранено как <code>Response 1</code></td>
    </tr>
    <tr>
        <td>2. Сохранить <code>user_id</code> из тела ответа как <code>{{createdUserId1}}</code></td>
        <td>Значение <code>user_id</code> сохранено как <code>{{createdUserId1}}</code></td>
    </tr>
    <tr>
        <td>3. Повторно отправить идентичный POST-запрос на <code>{{baseUrl}}/api/users</code> с телом запроса</td>
        <td>Статус-код: <code>201 Created</code><br>Тело ответа сохранено как <code>Response 2</code></td>
    </tr>
    <tr>
        <td>4. Сохранить <code>user_id</code> из тела ответа как <code>{{createdUserId2}}</code></td>
        <td>Значение <code>user_id</code> сохранено как <code>{{createdUserId2}}</code></td>
    </tr>
    <tr>
        <td>5. Сравнить <code>Response 1</code> и <code>Response 2</code></td>
        <td>Оба ответа содержат:<br> 
        - <code>first_name: Marla</code>,<br>
        - <code>last_name: Singer</code>,<br>
        - <code>company_id: {{activeCompanyId}}</code>.<br>
        Значения <code>user_id</code> различаются между собой и являются целыми положительными числами</td>
    </tr>
</table>

## USR-POST-011: Создание пользователя без необязательных полей first_name и company_id

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-POST-011</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Создание пользователя без необязательных полей <code>first_name</code> и <code>company_id</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Постусловие: </b>Отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><pre><code>{
  "last_name": "Durden"
}</code></pre></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить POST-запрос на <code>{{baseUrl}}/api/users</code> с телом запроса</td>
        <td>Статус-код: <code>201 Created</code></td>
    </tr>
    <tr>
        <td>2. Сохранить <code>user_id</code> из тела ответа как <code>{{createdUserId}}</code></td>
        <td>Значение <code>user_id</code> сохранено как <code>{{createdUserId}}</code></td>
    </tr>
    <tr>
        <td>3. Проверить время ответа сервера</td>
        <td>Время ответа сервера ≤ 500 ms</td>
    </tr>
    <tr>
        <td>4. Проверить заголовки ответа</td>
        <td><code>Content-Type: application/json</code></td>
    </tr>
    <tr>
        <td>5. Проверить структуру ответа (Schema Validation)</td>
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#responseuser">ResponseUser</a></td>
    </tr>
    <tr>
        <td>6. Проверить значения полей ответа</td>
        <td>- <code>first_name: null</code>,<br>
        - <code>last_name: Durden</code>,<br>
        - <code>company_id: null</code>,<br>
        - <code>user_id > 0</code>, сгенерировано сервером и является целым числом</td>
    </tr>
</table>

## USR-POST-012: Проверка обработки значения company_id = 0 при создании пользователя

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-POST-012</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки значения <code>company_id = 0</code> при создании пользователя</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><pre><code>{
  "first_name": "Tyler",
  "last_name": "Durden",
  "company_id": 0
}</code></pre></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить POST-запрос на <code>{{baseUrl}}/api/users</code> с телом запроса</td>
        <td>Статус-код: <code>404 Not Found</code></td>
    </tr>
    <tr>
        <td>2. Проверить время ответа сервера</td>
        <td>Время ответа сервера ≤ 500 ms</td>
    </tr>
    <tr>
        <td>3. Проверить заголовки ответа</td>
        <td><code>Content-Type: application/json</code></td>
    </tr>
    <tr>
        <td>4. Проверить структуру ответа (Schema Validation)</td>
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#errordetail">ErrorDetail</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>Объект <code>detail</code> содержит:<br>
        - <code>reason: Company with requested id: 0 is absent</code></td>
    </tr>
</table>

## USR-POST-013: Проверка обработки отрицательного числового значения поля company_id при создании пользователя

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-POST-013</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки отрицательного числового значения поля <code>company_id</code> при создании пользователя</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><pre><code>{
  "first_name": "Tyler",
  "last_name": "Durden",
  "company_id": -1
}</code></pre></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить POST-запрос на <code>{{baseUrl}}/api/users</code> с телом запроса</td>
        <td>Статус-код: <code>404 Not Found</code></td>
    </tr>
    <tr>
        <td>2. Проверить время ответа сервера</td>
        <td>Время ответа сервера ≤ 500 ms</td>
    </tr>
    <tr>
        <td>3. Проверить заголовки ответа</td>
        <td><code>Content-Type: application/json</code></td>
    </tr>
    <tr>
        <td>4. Проверить структуру ответа (Schema Validation)</td>
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#errordetail">ErrorDetail</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>Объект <code>detail</code> содержит:<br>
        - <code>reason: Company with requested id: -1 is absent</code></td>
    </tr>
</table>

## USR-POST-014: Проверка обработки строкового значения поля company_id при создании пользователя

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-POST-014</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки строкового значения поля company_id при создании пользователя</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><pre><code>{
  "first_name": "Tyler",
  "last_name": "Durden",
  "company_id": "first"
}</code></pre></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить POST-запрос на <code>{{baseUrl}}/api/users</code> с телом запроса</td>
        <td>Статус-код: <code>422 Unprocessable Entity</code></td>
    </tr>
    <tr>
        <td>2. Проверить время ответа сервера</td>
        <td>Время ответа сервера ≤ 500 ms</td>
    </tr>
    <tr>
        <td>3. Проверить заголовки ответа</td>
        <td><code>Content-Type: application/json</code></td>
    </tr>
    <tr>
        <td>4. Проверить структуру ответа (Schema Validation)</td>
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#httpvalidationerror">HTTPValidationError</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>В массиве <code>detail</code> объект содержит: <br>
        - <code>loc: [body, company_id]</code>, <br>
        - <code>msg: Input should be a valid integer, unable to parse string as an integer</code>, <br>
        - <code>type: int_parsing</code></td>
    </tr>
</table>

## USR-POST-015: Проверка обработки дробного значения поля company_id при создании пользователя

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-POST-015</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки дробного значения поля <code>company_id</code> при создании пользователя</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><pre><code>{
  "first_name": "Tyler",
  "last_name": "Durden",
  "company_id": 3.5
}</code></pre></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить POST-запрос на <code>{{baseUrl}}/api/users</code> с телом запроса</td>
        <td>Статус-код: <code>422 Unprocessable Entity</code></td>
    </tr>
    <tr>
        <td>2. Проверить время ответа сервера</td>
        <td>Время ответа сервера ≤ 500 ms</td>
    </tr>
    <tr>
        <td>3. Проверить заголовки ответа</td>
        <td><code>Content-Type: application/json</code></td>
    </tr>
    <tr>
        <td>4. Проверить структуру ответа (Schema Validation)</td>
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#httpvalidationerror">HTTPValidationError</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>В массиве <code>detail</code> объект содержит: <br>
        - <code>loc: [body, company_id]</code>, <br>
        - <code>msg: Input should be a valid integer, got a number with a fractional part</code>, <br>
        - <code>type: int_from_float</code></td>
    </tr>
</table>

## USR-POST-016: Проверка обработки числового значения поля first_name при создании пользователя

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-POST-016</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки числового значения поля <code>first_name</code> при создании пользователя</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>В базе данных существует активная компания с <code>company_id = {{activeCompanyId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><pre><code>{
  "first_name": 1,
  "last_name": "Durden",
  "company_id": {{activeCompanyId}}
}</code></pre></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить POST-запрос на <code>{{baseUrl}}/api/users</code> с телом запроса</td>
        <td>Статус-код: <code>422 Unprocessable Entity</code></td>
    </tr>
    <tr>
        <td>2. Проверить время ответа сервера</td>
        <td>Время ответа сервера ≤ 500 ms</td>
    </tr>
    <tr>
        <td>3. Проверить заголовки ответа</td>
        <td><code>Content-Type: application/json</code></td>
    </tr>
    <tr>
        <td>4. Проверить структуру ответа (Schema Validation)</td>
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#httpvalidationerror">HTTPValidationError</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>В массиве <code>detail</code> объект содержит: <br>
        - <code>loc: [body, first_name]</code>, <br>
        - <code>msg: Input should be a valid string</code>, <br>
        - <code>type: string_type</code></td>
    </tr>
</table>

## USR-POST-017: Проверка обработки числового значения поля last_name при создании пользователя

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-POST-017</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки числового значения поля <code>last_name</code> при создании пользователя</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>В базе данных существует активная компания с <code>company_id = {{activeCompanyId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><pre><code>{
  "first_name": "Tyler",
  "last_name": 2,
  "company_id": {{activeCompanyId}}
}</code></pre></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить POST-запрос на <code>{{baseUrl}}/api/users</code> с телом запроса</td>
        <td>Статус-код: <code>422 Unprocessable Entity</code></td>
    </tr>
    <tr>
        <td>2. Проверить время ответа сервера</td>
        <td>Время ответа сервера ≤ 500 ms</td>
    </tr>
    <tr>
        <td>3. Проверить заголовки ответа</td>
        <td><code>Content-Type: application/json</code></td>
    </tr>
    <tr>
        <td>4. Проверить структуру ответа (Schema Validation)</td>
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#httpvalidationerror">HTTPValidationError</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>В массиве <code>detail</code> объект содержит: <br>
        - <code>loc: [body, last_name]</code>, <br>
        - <code>msg: Input should be a valid string</code>, <br>
        - <code>type: string_type</code></td>
    </tr>
</table>

## USR-POST-018: Проверка обработки невалидного JSON в теле запроса при создании пользователя

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-POST-018</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки невалидного JSON в теле запроса при создании пользователя</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>В базе данных существует активная компания с <code>company_id = {{activeCompanyId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><pre><code>{
  "first_name": "Tyler",
  "last_name": "Durden",
  "company_id": {{activeCompanyId}}</code></pre></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить POST-запрос на <code>{{baseUrl}}/api/users</code> с невалидным телом запроса</td>
        <td>Статус-код: <code>422 Unprocessable Entity</code></td>
    </tr>
    <tr>
        <td>2. Проверить время ответа сервера</td>
        <td>Время ответа сервера ≤ 500 ms</td>
    </tr>
    <tr>
        <td>3. Проверить заголовки ответа</td>
        <td><code>Content-Type: application/json</code></td>
    </tr>
    <tr>
        <td>4. Проверить структуру ответа (Schema Validation)</td>
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#httpvalidationerror">HTTPValidationError</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>В массиве <code>detail</code> объект содержит: <br>
        - <code>loc: [body, &lt;integer&gt;]</code>, где число указывает позицию ошибки в теле запроса,<br>
        - <code>msg: JSON decode error</code>, <br>
        - <code>type: json_invalid</code></td>
    </tr>
</table>

## USR-POST-019: Проверка обработки запроса с заголовком Content-Type: application/xml при создании пользователя

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-POST-019</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки запроса с заголовком <code>Content-Type: application/xml</code> при создании пользователя</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>В базе данных существует активная компания с <code>company_id = {{activeCompanyId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b>
        <ol>
          <li>
            <pre><code>{
  "first_name": "Tyler",
  "last_name": "Durden",
  "company_id": {{activeCompanyId}}
}</code></pre>
          </li> 
          <li>
            <code>Content-Type: application/xml</code>
          </li>
        </ol></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить POST-запрос на <code>{{baseUrl}}/api/users</code> с JSON-телом и указанным значением заголовка Content-Type</td>
        <td>Статус-код: <code>422 Unprocessable Entity</code></td>
    </tr>
    <tr>
        <td>2. Проверить время ответа сервера</td>
        <td>Время ответа сервера ≤ 500 ms</td>
    </tr>
    <tr>
        <td>3. Проверить заголовки ответа</td>
        <td><code>Content-Type: application/json</code></td>
    </tr>
    <tr>
        <td>4. Проверить структуру ответа (Schema Validation)</td>
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#httpvalidationerror">HTTPValidationError</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>В массиве <code>detail</code> объект содержит: <br>
        - <code>loc: [body]</code>,<br>
        - <code>msg: Input should be a valid dictionary or object to extract fields from</code>, <br>
        - <code>type: model_attributes_type</code></td>
    </tr>
</table>

## USR-POST-020: Проверка обработки запроса без заголовка Content-Type при создании пользователя

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-POST-020</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки запроса без заголовка <code>Content-Type</code> при создании пользователя</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Needs Clarification</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>В базе данных существует активная компания с <code>company_id = {{activeCompanyId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Постусловие: </b>Если пользователь создан, сохранить <code>user_id</code> как <code>{{createdUserId}}</code> и отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><pre><code>{
  "first_name": "Tyler",
  "last_name": "Durden",
  "company_id": {{activeCompanyId}}
}</code></pre></td>
    </tr>
    <tr>
        <th rowspan="2">Шаги:</th>
        <td>1. Отправить POST-запрос на <code>{{baseUrl}}/api/users</code> с JSON-телом без заголовка <code>Content-Type</code></td>
    </tr>
    <tr>
        <td>2. Зафиксировать ответ сервера</td>
    </tr>
    <tr>
        <th>Ожидаемый результат</th>
        <th>Фактический результат</th>
    </tr>
    <tr>
        <td>Не определен требованиями</td>
        <td>Статус-код: <code>201 Created</code>.<br>
        Тело ответа содержит: <br>
        - <code>first_name: Tyler</code>,<br>
        - <code>last_name: Durden</code>,<br>
        - <code>company_id: {{activeCompanyId}}</code>,<br>
        - <code>user_id > 0</code>, сгенерировано сервером и является целым числом</td>
    </tr>
</table>

> _**Примечание**. Поведение запроса без заголовка <code>Content-Type</code> не описано в спецификации. По стандарту HTTP сервер вправе отклонить запрос без заголовка <code>Content-Type</code>. До уточнения требований тест-кейс не может быть оценён как Pass/Fail. Рекомендуется согласовать с разработчиком: либо сервер отклоняет запрос без <code>Content-Type</code>, либо принимает тело как JSON и создаёт пользователя._

## USR-POST-021: Проверка обработки дополнительного поля в теле запроса при создании пользователя

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-POST-021</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки дополнительного поля в теле запроса при создании пользователя</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Low</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>В базе данных существует активная компания с <code>company_id = {{activeCompanyId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Постусловие: </b>Отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><pre><code>{
  "first_name": "Tyler",
  "last_name": "Durden",
  "company_id": {{activeCompanyId}}, 
  "extra_field": "extra_value"
}</code></pre></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить POST-запрос на <code>{{baseUrl}}/api/users</code> с телом запроса</td>
        <td>Статус-код: <code>201 Created</code></td>
    </tr>
    <tr>
        <td>2. Сохранить <code>user_id</code> из тела ответа как <code>{{createdUserId}}</code></td>
        <td>Значение <code>user_id</code> сохранено как <code>{{createdUserId}}</code></td>
    </tr>
    <tr>
        <td>3. Проверить время ответа сервера</td>
        <td>Время ответа сервера ≤ 500 ms</td>
    </tr>
    <tr>
        <td>4. Проверить заголовки ответа</td>
        <td><code>Content-Type: application/json</code></td>
    </tr>
    <tr>
        <td>5. Проверить структуру ответа (Schema Validation)</td>
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#responseuser">ResponseUser</a></td>
    </tr>
    <tr>
        <td>6. Проверить значения полей ответа</td>
        <td>- <code>first_name: Tyler</code>,<br>
        - <code>last_name: Durden</code>,<br>
        - <code>company_id: {{activeCompanyId}}</code>,<br>
        - <code>user_id > 0</code>, сгенерировано сервером и является целым числом. <br>
        Поле <code>extra_field</code> в ответе отсутствует, сервер игнорирует неизвестные поля</td>
    </tr>
</table>

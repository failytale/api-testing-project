# Test Cases — DELETE /api/users/{user_id}

## USR-DEL-001: Удаление существующего пользователя по user_id

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-DEL-001</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Удаление существующего пользователя по <code>user_id</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>High</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Fail</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>
        <ol>
            <li>Создать тестового пользователя с привязкой к активной компании с помощью POST-запроса на <code>{{baseUrl}}/api/users</code> с телом запроса: <pre><code>{
  "first_name": "User",
  "last_name": "Test",
  "company_id": {{activeCompanyId}}
}</code></pre></li>
            <li>Сохранить <code>user_id</code> из тела ответа созданного пользователя как <code>{{createdUserId}}</code></li>
        </ol>
        </td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>user_id = {{createdUserId}}</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code></td>
        <td>Статус-код: <code>202 Accepted</code></td>
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
        <td>4. Проверить тело ответа</td>
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#deleteuserresponse">DeleteUserResponse
</a> и не является <code>null</code></td>
    </tr>
    <tr>
        <td>5. Отправить GET-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code> для проверки удаления</td>
        <td>Статус-код: <code>404 Not Found</code></td>
    </tr>
</table>

## USR-DEL-002: Проверка повторного удаления ранее удалённого пользователя

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-DEL-002</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка повторного удаления ранее удалённого пользователя</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>High</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>
        <ol>
            <li>Создать тестового пользователя с привязкой к активной компании с помощью POST-запроса на <code>{{baseUrl}}/api/users</code> с телом запроса: <pre><code>{
  "first_name": "User",
  "last_name": "Test",
  "company_id": {{activeCompanyId}}
}</code></pre></li>
            <li>Сохранить <code>user_id</code> из тела ответа созданного пользователя как <code>{{createdUserId}}</code></li>
        </ol>
        </td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>user_id = {{createdUserId}}</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code></td>
        <td>Статус-код: <code>202 Accepted</code></td>
    </tr>
    <tr>
        <td>2. Повторно отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code></td>
        <td>Статус-код: <code>404 Not Found</code></td>
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
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#errordetail">ErrorDetail</a></td>
    </tr>
    <tr>
        <td>6. Проверить значения полей ответа</td>
        <td>Объект <code>detail</code> содержит:<br>
        - <code>reason: User with requested id: &lt;createdUserId&gt; is absent</code></td>
    </tr>
</table>

## USR-ID-003: Проверка удаления пользователя с несуществующим значением user_id

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-ID-003</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка удаления пользователя с несуществующим значением <code>user_id</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>High</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>В базе данных отсутствует пользователь с <code>user_id = {{nonexistentUserId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>user_id = {{nonexistentUserId}}</code>
        </td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{{nonexistentUserId}}</code></td>
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
        - <code>reason: User with requested id: &lt;nonexistentUserId&gt; is absent</code></td>
    </tr>
</table>

## USR-DEL-004: Проверка обработки строкового значения параметра пути user_id при удалении пользователя

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-DEL-004</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки строкового значения параметра пути <code>user_id</code> при удалении пользователя</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>user_id = abc</code>
        </td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{user_id}</code> c указанным значением path-параметра</td>
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
        - <code>loc: [path, user_id]</code>, <br>
        - <code>msg: Input should be a valid integer, unable to parse string as an integer</code>, <br>
        - <code>type: int_parsing</code></td>
    </tr>
</table>

## USR-DEL-005: Проверка обработки значения user_id = 0 при удалении пользователя

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-DEL-005</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки значения <code>user_id = 0</code> при удалении пользователя</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>user_id = 0</code>
        </td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{user_id}</code><br> c указанным значением path-параметра</td>
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
        - <code>reason: User with requested id: 0 is absent</code></td>
    </tr>
</table>

## USR-DEL-006: Проверка обработки отрицательного числового значения параметра пути user_id при удалении пользователя

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-DEL-006</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки отрицательного числового значения параметра пути <code>user_id</code> при удалении пользователя</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>user_id = -1</code>
        </td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{user_id}</code><br> c указанным значением path-параметра</td>
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
        - <code>reason: User with requested id: -1 is absent</code></td>
    </tr>
</table>

## USR-DEL-007: Проверка обработки дробного значения параметра пути user_id при удалении пользователя

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-DEL-007</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки дробного значения параметра пути <code>user_id</code> при удалении пользователя</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>user_id = 210.5</code>
        </td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{user_id}</code> c указанным значением path-параметра</td>
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
        - <code>loc: [path, user_id]</code>, <br>
        - <code>msg: Input should be a valid integer, unable to parse string as an integer</code>, <br>
        - <code>type: int_parsing</code></td>
    </tr>
</table>

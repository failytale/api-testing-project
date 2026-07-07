# Test Cases — PUT /api/users/{user_id}

## USR-PUT-001: Обновление пользователя с валидными значениями всех полей

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-PUT-001</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Обновление пользователя с валидными значениями всех полей</td>
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
            <li>В базе данных существует активная компания с <code>company_id = {{activeCompanyId}}</code></li>
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
        <td colspan="2"><b>Постусловие: </b>Отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b>
          <ol>
            <li><pre><code>{
  "first_name": "Robert",
  "last_name": "Paulson",
  "company_id": {{activeCompanyId}}
}</code></pre></li>
            <li><code>user_id = {{createdUserId}}</code></li>
          </ol>
        </td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить PUT-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code><br> с телом запроса</td>
        <td>Статус-код: <code>200 OK</code></td>
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
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#responseuser">ResponseUser</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>- <code>first_name: Robert</code>,<br>
        - <code>last_name: Paulson</code>,<br>
        - <code>company_id: {{activeCompanyId}}</code>.<br>
        Значение <code>user_id</code> совпадает с переданным в URI</td>
    </tr>
</table>

## USR-PUT-002: Обновление пользователя со значением first_name = null

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-PUT-002</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Обновление пользователя со значением <code>first_name = null</code></td>
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
            <li>В базе данных существует активная компания с <code>company_id = {{activeCompanyId}}</code></li>
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
        <td colspan="2"><b>Постусловие: </b>Отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b>
          <ol>
            <li><pre><code>{
  "first_name": null,
  "last_name": "Paulson",
  "company_id": {{activeCompanyId}}
}</code></pre></li>
            <li><code>user_id = {{createdUserId}}</code></li>
          </ol>
        </td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить PUT-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code><br> с телом запроса</td>
        <td>Статус-код: <code>200 OK</code></td>
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
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#responseuser">ResponseUser</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>- <code>first_name: null</code>,<br>
        - <code>last_name: Paulson</code>,<br>
        - <code>company_id: {{activeCompanyId}}</code>.<br>
        Значение <code>user_id</code> совпадает с переданным в URI</td>
    </tr>
</table>

## USR-PUT-003: Обновление пользователя со значением company_id = null

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-PUT-003</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Обновление пользователя со значением <code>company_id = null</code></td>
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
        <td colspan="2"><b>Постусловие: </b>Отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b>
          <ol>
            <li><pre><code>{
  "first_name": "Robert",
  "last_name": "Paulson",
  "company_id": null
}</code></pre></li>
            <li><code>user_id = {{createdUserId}}</code></li>
          </ol>
        </td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить PUT-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code><br> с телом запроса</td>
        <td>Статус-код: <code>200 OK</code></td>
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
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#responseuser">ResponseUser</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>- <code>first_name: Robert</code>,<br>
        - <code>last_name: Paulson</code>,<br>
        - <code>company_id: null</code>.<br>
        Значение <code>user_id</code> совпадает с переданным в URI</td>
    </tr>
</table>

## USR-PUT-004: Проверка обработки значения last_name = null при обновлении пользователя

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-PUT-004</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки значения <code>last_name = null</code> при обновлении пользователя</td>
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
            <li>В базе данных существует активная компания с <code>company_id = {{activeCompanyId}}</code></li>
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
        <td colspan="2"><b>Постусловие: </b>Отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b>
          <ol>
            <li><pre><code>{
  "first_name": "Robert",
  "last_name": null,
  "company_id": {{activeCompanyId}}
}</code></pre></li>
            <li><code>user_id = {{createdUserId}}</code></li>
          </ol>
        </td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить PUT-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code> с телом запроса</td>
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

## USR-PUT-005: Проверка обработки попытки обновления пользователя с привязкой к компании со статусом "CLOSED"

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-PUT-005</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки попытки обновления пользователя с привязкой к компании со статусом <code>CLOSED</code></td>
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
            <li>В базе данных существует закрытая компания с <code>company_id = {{closedCompanyId}}</code></li>
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
        <td colspan="2"><b>Постусловие: </b>Отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b>
          <ol>
            <li><pre><code>{
  "first_name": "Robert",
  "last_name": "Paulson",
  "company_id": {{closedCompanyId}}
}</code></pre></li>
            <li><code>user_id = {{createdUserId}}</code></li>
          </ol>
        </td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить PUT-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code> с телом запроса</td>
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

## USR-PUT-006: Проверка обработки попытки обновления пользователя с привязкой к компании со статусом "BANKRUPT"

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-PUT-006</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки попытки обновления пользователя с привязкой к компании со статусом <code>BANKRUPT</code></td>
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
            <li>В базе данных существует обанкротившаяся компания с <code>company_id = {{bankruptCompanyId}}</code></li>
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
        <td colspan="2"><b>Постусловие: </b>Отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b>
          <ol>
            <li><pre><code>{
  "first_name": "Robert",
  "last_name": "Paulson",
  "company_id": {{bankruptCompanyId}}
}</code></pre></li>
            <li><code>user_id = {{createdUserId}}</code></li>
          </ol>
        </td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить PUT-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code> с телом запроса</td>
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

## USR-PUT-007: Проверка обработки попытки обновления несуществующего пользователя

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-PUT-007</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки попытки обновления несуществующего пользователя</td>
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
            <li>В базе данных существует активная компания с <code>company_id = {{activeCompanyId}}</code></li>
            <li>В базе данных отсутствует пользователь с <code>user_id = {{nonexistentUserId}}</code></li>
        </ol>
        </td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b>
          <ol>
            <li><pre><code>{
  "first_name": "Robert",
  "last_name": "Paulson",
  "company_id": {{activeCompanyId}}
}</code></pre></li>
            <li><code>user_id = {{nonexistentUserId}}</code></li>
          </ol>
        </td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить PUT-запрос на <code>{{baseUrl}}/api/users/{{nonexistentUserId}}</code> с телом запроса</td>
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

## USR-PUT-008: Проверка обработки попытки обновления пользователя с несуществующим значением company_id

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-PUT-008</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки попытки обновления пользователя с несуществующим значением <code>company_id</code></td>
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
            <li>В базе данных отсутствует компания с <code>company_id = {{nonexistentCompanyId}}</code></li>
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
        <td colspan="2"><b>Постусловие: </b>Отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b>
          <ol>
            <li><pre><code>{
  "first_name": "Robert",
  "last_name": "Paulson",
  "company_id": {{nonexistentCompanyId}}
}</code></pre></li>
            <li><code>user_id = {{createdUserId}}</code></li>
          </ol>
        </td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить PUT-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code><br> с телом запроса</td>
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

## USR-PUT-009: Проверка обработки запроса на обновление без обязательного поля last_name

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-PUT-009</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки запроса на обновление без обязательного поля <code>last_name</code></td>
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
            <li>В базе данных существует активная компания с <code>company_id = {{activeCompanyId}}</code></li>
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
        <td colspan="2"><b>Постусловие: </b>Отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b>
          <ol>
            <li><pre><code>{
  "first_name": "Robert",
  "company_id": {{activeCompanyId}}
}</code></pre></li>
            <li><code>user_id = {{createdUserId}}</code></li>
          </ol>
        </td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить PUT-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code> с телом запроса</td>
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

## USR-PUT-010: Проверка обработки запроса на обновление пользователя без тела запроса

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-PUT-010</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки запроса на обновление пользователя без тела запроса</td>
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
        <td colspan="2"><b>Постусловие: </b>Отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>user_id = {{createdUserId}}</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить PUT-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code> без тела запроса</td>
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

## USR-PUT-011: Проверка идемпотентности повторного PUT-запроса с одинаковым телом запроса

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-PUT-011</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка идемпотентности повторного PUT-запроса с одинаковым телом запроса</td>
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
            <li>В базе данных существует активная компания с <code>company_id = {{activeCompanyId}}</code></li>
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
        <td colspan="2"><b>Постусловие: </b>Отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b>
          <ol>
            <li><pre><code>{
  "first_name": "Richard",
  "last_name": "Chesler",
  "company_id": {{activeCompanyId}}
}</code></pre></li>
            <li><code>user_id = {{createdUserId}}</code></li>
          </ol>
        </td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить PUT-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code> с телом запроса</td>
        <td>Статус-код: <code>200 OK</code>. Тело ответа сохранено как <code>Response 1</code></td>
    </tr>
    <tr>
        <td>2. Повторно отправить идентичный PUT-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code> с телом запроса</td>
        <td>Статус-код: <code>200 OK</code>. Тело ответа сохранено как <code>Response 2</code></td>
    </tr>
    <tr>
        <td>3. Повторно отправить идентичный PUT-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code> с телом запроса</td>
        <td>Статус-код: <code>200 OK</code>. Тело ответа сохранено как <code>Response 3</code></td>
    </tr>
    <tr>
        <td>4. Сравнить <code>Response 1</code>, <code>Response 2</code> и <code>Response 3</code></td>
        <td>Тела ответов <code>Response 1</code>, <code>Response 2</code> и <code>Response 3</code> идентичны.<br>
            Совпадают значения: <code>first_name</code>, <code>last_name</code>, <code>company_id</code>, <code>user_id</code>.<br>
            Несколько одинаковых PUT-запросов приводят ресурс к одному и тому же состоянию</td>
    </tr>
</table>

## USR-PUT-012: Проверка обработки строкового значения параметра пути user_id при обновлении пользователя

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-PUT-012</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки строкового значения параметра пути <code>user_id</code> при обновлении пользователя</td>
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
            <li><pre><code>{
  "first_name": "Robert",
  "last_name": "Paulson",
  "company_id": {{activeCompanyId}}
}</code></pre></li>
            <li><code>user_id = abc</code></li>
          </ol>
        </td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить PUT-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code> c указанным значением path-параметра и телом запроса</td>
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

## USR-PUT-013: Обновление пользователя без необязательных полей first_name и company_id

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-PUT-013</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Обновление пользователя без необязательных полей <code>first_name</code> и <code>company_id</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
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
        <td colspan="2"><b>Постусловие: </b>Отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b>
          <ol>
            <li><pre><code>{
  "last_name": "Paulson"
}</code></pre></li>
            <li><code>user_id = {{createdUserId}}</code></li>
          </ol>
        </td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить PUT-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code><br> с телом запроса</td>
        <td>Статус-код: <code>200 OK</code></td>
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
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#responseuser">ResponseUser</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>- <code>first_name: null</code>,<br>
        - <code>last_name: Paulson</code>,<br>
        - <code>company_id: null</code>.<br>
        Значение <code>user_id</code> совпадает с переданным в URI</td>
    </tr>
</table>

## USR-PUT-014: Проверка обработки числового значения поля first_name при обновлении пользователя

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-PUT-014</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки числового значения поля <code>first_name</code> при обновлении пользователя</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>
        <ol>
            <li>В базе данных существует активная компания с <code>company_id = {{activeCompanyId}}</code></li>
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
        <td colspan="2"><b>Постусловие: </b>Отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b>
          <ol>
            <li><pre><code>{
  "first_name": 1,
  "last_name": "Paulson",
  "company_id": {{activeCompanyId}}
}</code></pre></li>
            <li><code>user_id = {{createdUserId}}</code></li>
          </ol>
        </td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить PUT-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code><br> с телом запроса</td>
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

## USR-PUT-015: Проверка обработки числового значения поля last_name при обновлении пользователя

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-PUT-015</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки числового значения поля <code>last_name</code> при обновлении пользователя</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>
        <ol>
            <li>В базе данных существует активная компания с <code>company_id = {{activeCompanyId}}</code></li>
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
        <td colspan="2"><b>Постусловие: </b>Отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b>
          <ol>
            <li><pre><code>{
  "first_name": "Robert",
  "last_name": 2,
  "company_id": {{activeCompanyId}}
}</code></pre></li>
            <li><code>user_id = {{createdUserId}}</code></li>
          </ol>
        </td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить PUT-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code><br> с телом запроса</td>
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

## USR-PUT-016: Проверка обработки значения user_id = 0 при обновлении пользователя

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-PUT-016</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки значения <code>user_id = 0</code> при обновлении пользователя</td>
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
            <li><pre><code>{
  "first_name": "Robert",
  "last_name": "Paulson",
  "company_id": {{activeCompanyId}}
}</code></pre></li>
            <li><code>user_id = 0</code></li>
          </ol>
        </td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить PUT-запрос на <code>{{baseUrl}}/api/users/{user_id}</code><br> c указанным значением path-параметра и телом запроса</td>
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

## USR-PUT-017: Проверка обработки отрицательного числового значения параметра пути user_id при обновлении пользователя

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-PUT-017</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки отрицательного числового значения параметра пути <code>user_id</code> при обновлении пользователя</td>
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
            <li><pre><code>{
  "first_name": "Robert",
  "last_name": "Paulson",
  "company_id": {{activeCompanyId}}
}</code></pre></li>
            <li><code>user_id = -1</code></li>
          </ol>
        </td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить PUT-запрос на <code>{{baseUrl}}/api/users/{user_id}</code><br> c указанным значением path-параметра и телом запроса</td>
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

## USR-PUT-018: Проверка обработки дробного значения параметра пути user_id при обновлении пользователя

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-PUT-018</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки дробного значения параметра пути <code>user_id</code> при обновлении пользователя</td>
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
            <li><pre><code>{
  "first_name": "Robert",
  "last_name": "Paulson",
  "company_id": {{activeCompanyId}}
}</code></pre></li>
            <li><code>user_id = 210.5</code></li>
          </ol>
        </td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить PUT-запрос на <code>{{baseUrl}}/api/users/{user_id}</code> c указанным значением path-параметра и телом запроса</td>
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

## USR-PUT-019: Проверка обработки значения company_id = 0 при обновлении пользователя

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-PUT-019</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки значения <code>company_id = 0</code> при обновлении пользователя</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
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
        <td colspan="2"><b>Постусловие: </b>Отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b>
          <ol>
            <li><pre><code>{
  "first_name": "Robert",
  "last_name": "Paulson",
  "company_id": 0
}</code></pre></li>
            <li><code>user_id = {{createdUserId}}</code></li>
          </ol>
        </td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить PUT-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code><br> с телом запроса</td>
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

## USR-PUT-020: Проверка обработки отрицательного числового значения поля company_id при обновлении пользователя

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-PUT-020</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки отрицательного числового значения поля <code>company_id</code> при обновлении пользователя</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
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
        <td colspan="2"><b>Постусловие: </b>Отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b>
          <ol>
            <li><pre><code>{
  "first_name": "Robert",
  "last_name": "Paulson",
  "company_id": -1
}</code></pre></li>
            <li><code>user_id = {{createdUserId}}</code></li>
          </ol>
        </td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить PUT-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code><br> с телом запроса</td>
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

## USR-PUT-021: Проверка обработки строкового значения поля company_id при обновлении пользователя

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-PUT-021</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки строкового значения поля <code>company_id</code> при обновлении пользователя</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
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
        <td colspan="2"><b>Постусловие: </b>Отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b>
          <ol>
            <li><pre><code>{
  "first_name": "Robert",
  "last_name": "Paulson",
  "company_id": "any_string"
}</code></pre></li>
            <li><code>user_id = {{createdUserId}}</code></li>
          </ol>
        </td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить PUT-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code> с телом запроса</td>
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

## USR-PUT-022: Проверка обработки дробного значения поля company_id при обновлении пользователя

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-PUT-022</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки дробного значения поля <code>company_id</code> при обновлении пользователя</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
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
        <td colspan="2"><b>Постусловие: </b>Отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b>
          <ol>
            <li><pre><code>{
  "first_name": "Robert",
  "last_name": "Paulson",
  "company_id": 3.5
}</code></pre></li>
            <li><code>user_id = {{createdUserId}}</code></li>
          </ol>
        </td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить PUT-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code> с телом запроса</td>
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

## USR-PUT-023: Проверка обработки запроса на обновление без заголовка Content-Type

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-PUT-023</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки запроса на обновление без заголовка <code>Content-Type</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Needs Clarification</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>
        <ol>
            <li>В базе данных существует активная компания с <code>company_id = {{activeCompanyId}}</code></li>
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
        <td colspan="2"><b>Постусловие: </b>Отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b>
          <ol>
            <li><pre><code>{
  "first_name": "Robert",
  "last_name": "Paulson",
  "company_id": {{activeCompanyId}}
}</code></pre></li>
            <li><code>user_id = {{createdUserId}}</code></li>
          </ol>
        </td>
    </tr>
    <tr>
        <th rowspan="2">Шаги:</th>
        <td>1. Отправить PUT-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code> с JSON-телом без заголовка <code>Content-Type</code></td>
    </tr>
    <tr>
        <td>2. Зафиксировать ответ сервера</td>
    </tr>
    <tr>
        <th>Ожидаемый результат</th>
        <th>Фактический результат</th>
    </tr>
    <tr>
        <td nowrap>Не определен требованиями</td>
        <td>Статус-код: <code>200 OK</code>.<br>
        Тело ответа содержит: <br>
        - <code>first_name: Robert</code>,<br>
        - <code>last_name: Paulson</code>,<br>
        - <code>company_id: {{activeCompanyId}}</code>,<br>
        Значение <code>user_id</code> совпадает с переданным в URI</td>
    </tr>
</table>

> _**Примечание**. Поведение запроса без заголовка <code>Content-Type</code> не описано в спецификации. По стандарту HTTP сервер вправе отклонить запрос без заголовка <code>Content-Type</code>. До уточнения требований тест-кейс не может быть оценён как Pass/Fail. Рекомендуется согласовать с разработчиком: либо сервер отклоняет запрос без <code>Content-Type</code>, либо принимает тело как JSON и обновляет пользователя._

## USR-PUT-024: Проверка обработки запроса на обновление с заголовком Content-Type: application/xml

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-PUT-024</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки запроса на обновление с заголовком <code>Content-Type: application/xml</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>
        <ol>
            <li>В базе данных существует активная компания с <code>company_id = {{activeCompanyId}}</code></li>
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
        <td colspan="2"><b>Постусловие: </b>Отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b>
          <ol>
            <li><pre><code>{
  "first_name": "Robert",
  "last_name": "Paulson",
  "company_id": {{activeCompanyId}}
}</code></pre></li>
            <li><code>user_id = {{createdUserId}}</code></li>
            <li><code>Content-Type: application/xml</code></li>
          </ol>
        </td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить PUT-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code> с JSON-телом и указанным значением заголовка Content-Type</td>
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

## USR-PUT-025: Проверка обработки невалидного JSON в теле запроса при обновлении пользователя

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-PUT-025</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки невалидного JSON в теле запроса при обновлении пользователя</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>
        <ol>
            <li>В базе данных существует активная компания с <code>company_id = {{activeCompanyId}}</code></li>
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
        <td colspan="2"><b>Постусловие: </b>Отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b>
          <ol>
            <li><pre><code>{
  "first_name": "Robert",
  "last_name": "Paulson",
  "company_id": {{activeCompanyId}}
</code></pre></li>
            <li><code>user_id = {{createdUserId}}</code></li>
          </ol>
        </td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить PUT-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code> с невалидным телом запроса</td>
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

## USR-PUT-026: Проверка обработки дополнительного поля в теле запроса при обновлении пользователя

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-PUT-026</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки дополнительного поля в теле запроса при обновлении пользователя</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Low</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>
        <ol>
            <li>В базе данных существует активная компания с <code>company_id = {{activeCompanyId}}</code></li>
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
        <td colspan="2"><b>Постусловие: </b>Отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b>
          <ol>
            <li><pre><code>{
  "first_name": "Robert",
  "last_name": "Paulson",
  "company_id": {{activeCompanyId}}, 
  "extra_field": "extra_value"
}</code></pre></li>
            <li><code>user_id = {{createdUserId}}</code></li>
          </ol>
        </td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить PUT-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code> с телом запроса</td>
        <td>Статус-код: <code>200 OK</code></td>
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
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#responseuser">ResponseUser</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>- <code>first_name: Robert</code>,<br>
        - <code>last_name: Paulson</code>,<br>
        - <code>company_id: {{activeCompanyId}}</code>.<br>
        Значение <code>user_id</code> совпадает с переданным в URI.<br>
        Поле <code>extra_field</code> в ответе отсутствует, сервер игнорирует неизвестные поля</td>
    </tr>
</table>

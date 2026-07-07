# Test Cases — GET /api/users/{user_id}

## USR-ID-001: Получение информации о существующем пользователе по user_id

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-ID-001</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Получение информации о существующем пользователе по <code>user_id</code></code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>High</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>В базе данных существует пользователь с <code>user_id = {{existingUserId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>user_id = {{existingUserId}}</code>
        </td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/users/{{existingUserId}}</code></td>
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
        <td>Значение <code>user_id</code> совпадает с переданным в URI.<br>Ключи <code>first_name</code>, <code>last_name</code>, <code>company_id</code> содержат значения соответствующих типов согласно схеме</td>
    </tr>
</table>

## USR-ID-002: Проверка обработки несуществующего значения параметра пути user_id при получении информации о пользователе

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-ID-002</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки несуществующего значения параметра пути <code>user_id</code> при получении информации о пользователе</td>
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
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/users/{{nonexistentUserId}}</code></td>
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

## USR-ID-003: Проверка обработки значения user_id = 0 при получении информации о пользователе

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-ID-003</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки значения <code>user_id = 0</code> при получении информации о пользователе</td>
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
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/users/{user_id}</code> c указанным значением path-параметра</td>
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

## USR-ID-004: Проверка обработки отрицательного числового значения параметра пути user_id при получении информации о пользователе

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-ID-004</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки отрицательного числового значения параметра пути <code>user_id</code> при получении информации о пользователе</td>
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
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/users/{user_id}</code> c указанным значением path-параметра</td>
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

## USR-ID-005: Проверка обработки строкового значения параметра пути user_id при получении информации о пользователе

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-ID-005</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки строкового значения параметра пути <code>user_id</code> при получении информации о пользователе</td>
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
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/users/{user_id}</code> c указанным значением path-параметра</td>
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

## USR-ID-006: Проверка обработки дробного значения параметра пути user_id при получении информации о пользователе

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-ID-006</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки дробного значения параметра пути <code>user_id</code> при получении информации о пользователе</td>
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
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/users/{user_id}</code> c указанным значением path-параметра</td>
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

## USR-ID-007: Проверка отсутствия изменения состояния при повторном GET-запросе с одинаковым user_id при получении информации о пользователе

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-ID-007</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка отсутствия изменения состояния при повторном GET-запросе с одинаковым <code>user_id</code> при получении информации о пользователе</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Low</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>В базе данных существует пользователь с <code>user_id = {{existingUserId}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>user_id = {{existingUserId}}</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/users/{{existingUserId}}</code></td>
        <td>Статус-код: <code>200 OK</code>.<br>Тело ответа сохранено как <code>Response 1</code></td>
    </tr>
    <tr>
        <td>2. Повторно отправить идентичный GET-запрос на <code>{{baseUrl}}/api/users/{{existingUserId}}</code></td>
        <td>Статус-код: <code>200 OK</code>.<br>Тело ответа сохранено как <code>Response 2</code></td>
    </tr>
    <tr>
        <td>3. Сравнить <code>Response 1</code> и <code>Response 2</code></td>
        <td>Тела ответов <code>Response 1</code> и <code>Response 2</code> идентичны.<br>Совпадают значения: <code>first_name</code>, <code>last_name</code>, <code>company_id</code>, <code>user_id</code></td>
    </tr>
</table>

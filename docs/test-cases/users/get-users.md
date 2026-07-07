# Test Cases — GET /api/users

## USR-LIST-001: Получение списка пользователей без query-параметров

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-LIST-001</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Получение списка пользователей без query-параметров</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>High</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>База данных содержит не менее 3-х пользователей</td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/users</code></td>
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
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#userslist">UsersList</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>Объект <code>meta</code> содержит: <br>
        - <code>total: &lt;фактическое количество пользователей в БД&gt;</code>, <br>
        - <code>limit: 3</code>, <br>
        - <code>offset: 0</code>.<br>
        Массив <code>data</code> содержит 3 объекта</td>
    </tr>
</table>

## USR-LIST-002: Получение списка пользователей с корректным значением query-параметра limit

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-LIST-002</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Получение списка пользователей с корректным значением query-параметра <code>limit</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>High</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>База данных содержит не менее 5-ти пользователей</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>limit=5</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/users</code> с указанным значением query-параметра</td>
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
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#userslist">UsersList</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>Объект <code>meta</code> содержит: <br>
        - <code>total: &lt;фактическое количество пользователей в БД&gt;</code>, <br>
        - <code>limit: 5</code>, <br>
        - <code>offset: 0</code>.<br>
        Массив <code>data</code> содержит ровно 5 объектов</td>
    </tr>
</table>

## USR-LIST-003: Получение списка пользователей с минимально допустимым значением query-параметра limit

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-LIST-003</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Получение списка пользователей с минимально допустимым значением query-параметра <code>limit</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>High</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>База данных содержит не менее 1-го пользователя</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>limit=1</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/users</code> с указанным значением query-параметра</td>
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
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#userslist">UsersList</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>Объект <code>meta</code> содержит: <br>
        - <code>total: &lt;фактическое количество пользователей в БД&gt;</code>, <br>
        - <code>limit: 1</code>, <br>
        - <code>offset: 0</code>.<br>
        Массив <code>data</code> содержит ровно 1 объект</td>
    </tr>
</table>

## USR-LIST-004: Проверка обработки значения limit = 0 при получении списка пользователей

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-LIST-004</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки значения <code>limit = 0</code> при получении списка пользователей</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>High</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Fail</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>limit=0</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/users</code> с указанным значением query-параметра</td>
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
        - <code>loc: [query, limit]</code>, <br>
        - <code>msg: &lt;validation message&gt;</code>, <br>
        - <code>type: &lt;validation error type&gt;</code></td>
    </tr>
</table>

## USR-LIST-005: Проверка обработки отрицательного числового значения query-параметра limit при получении списка пользователей

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-LIST-005</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки отрицательного числового значения query-параметра <code>limit</code> при получении списка пользователей</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>High</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Fail</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>limit=-1</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/users</code> с указанным значением query-параметра</td>
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
        - <code>loc: [query, limit]</code>, <br>
        - <code>msg: &lt;validation message&gt;</code>, <br>
        - <code>type: &lt;validation error type&gt;</code></td>
    </tr>
</table>

## USR-LIST-006: Получение списка пользователей с корректным значением query-параметра offset

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-LIST-006</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Получение списка пользователей с корректным значением query-параметра <code>offset</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>High</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>База данных содержит более 10-ти пользователей</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>offset=10</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/users</code> с указанным значением query-параметра</td>
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
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#userslist">UsersList</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>Объект <code>meta</code> содержит: <br>
        - <code>total: &lt;фактическое количество пользователей в БД&gt;</code>, <br>
        - <code>limit: 3</code>, <br>
        - <code>offset: 10</code>.<br>
        Массив <code>data</code> не содержит первые 10 записей из полного списка пользователей</td>
    </tr>
</table>

## USR-LIST-007: Получение списка пользователей при значении offset, равном или превышающем total

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-LIST-007</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Получение списка пользователей при значении <code>offset</code>, равном или превышающем <code>total</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>High</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>Общее количество пользователей в базе данных не превышает 99999</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>offset=99999</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/users</code> с указанным значением query-параметра</td>
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
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#userslist">UsersList</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>Объект <code>meta</code> содержит: <br>
        - <code>total: &lt;фактическое количество пользователей в БД&gt;</code>, <br>
        - <code>limit: 3</code>, <br>
        - <code>offset: 99999</code>.<br>
        Массив <code>data</code> пустой (<code>[]</code>)</td>
    </tr>
</table>

## USR-LIST-008: Проверка обработки отрицательного числового значения query-параметра offset при получении списка пользователей

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-LIST-008</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки отрицательного числового значения query-параметра <code>offset</code> при получении списка пользователей</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>High</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Needs Clarification</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>offset=-1</code></td>
    </tr>
    <tr>
        <th rowspan="2">Шаги:</th>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/users</code> с указанным значением query-параметра</td>
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
        <td>Статус-код: <code>200 OK</code>.<br>
        Объект <code>meta</code> содержит: <br>
        - <code>total: &lt;фактическое количество компаний в БД&gt;</code>, <br>
        - <code>limit: 3</code>, <br>
        - <code>offset: -1</code><br>
        Массив <code>data</code> содержит 3 объекта, начиная с первой записи</td>
    </tr>
</table>

> _**Примечание**. Поведение при отрицательном значении <code>offset</code> не задокументировано в спецификации. До уточнения требований тест-кейс не может быть оценён как Pass/Fail. Рекомендуется согласовать с разработчиком, ожидается ли 422 или описанное фактическое поведение._

## USR-LIST-009: Проверка обработки строкового значения query-параметра limit при получении списка пользователей

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-LIST-009</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки строкового значения query-параметра <code>limit</code> при получении списка пользователей</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>limit=abc</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/users</code> с указанным значением query-параметра</td>
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
        - <code>loc: [query, limit]</code>, <br>
        - <code>msg: Input should be a valid integer, unable to parse string as an integer</code>, <br>
        - <code>type: int_parsing</code></td>
    </tr>
</table>

## USR-LIST-010: Проверка обработки пустого значения query-параметра limit при получении списка пользователей

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-LIST-010</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки пустого значения query-параметра <code>limit</code> при получении списка пользователей</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>limit=пустое значение</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/users</code> с указанным значением query-параметра</td>
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
        - <code>loc: [query, limit]</code>, <br>
        - <code>msg: Input should be a valid integer, unable to parse string as an integer</code>, <br>
        - <code>type: int_parsing</code></td>
    </tr>
</table>

## USR-LIST-011: Проверка обработки дробного значения query-параметра limit при получении списка пользователей

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-LIST-011</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки дробного значения query-параметра <code>limit</code> при получении списка пользователей</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>limit=2.5</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/users</code> с указанным значением query-параметра</td>
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
        - <code>loc: [query, limit]</code>, <br>
        - <code>msg: Input should be a valid integer, unable to parse string as an integer</code>, <br>
        - <code>type: int_parsing</code></td>
    </tr>
</table>

## USR-LIST-012: Проверка обработки строкового значения query-параметра offset при получении списка пользователей

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-LIST-012</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки строкового значения query-параметра <code>offset</code> при получении списка пользователей</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>offset=abc</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/users</code> с указанным значением query-параметра</td>
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
        - <code>loc: [query, offset]</code>, <br>
        - <code>msg: Input should be a valid integer, unable to parse string as an integer</code>, <br>
        - <code>type: int_parsing</code></td>
    </tr>
</table>

## USR-LIST-013: Проверка обработки пустого значения query-параметра offset при получении списка пользователей

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-LIST-013</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки пустого значения query-параметра <code>offset</code> при получении списка пользователей</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>offset=пустое значение</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/users</code> с указанным значением query-параметра</td>
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
        - <code>loc: [query, offset]</code>, <br>
        - <code>msg: Input should be a valid integer, unable to parse string as an integer</code>, <br>
        - <code>type: int_parsing</code></td>
    </tr>
</table>

## USR-LIST-014: Проверка обработки дробного значения query-параметра offset при получении списка пользователей

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-LIST-014</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки дробного значения query-параметра <code>offset</code> при получении списка пользователей</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>offset=3.5</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/users</code> с указанным значением query-параметра</td>
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
        - <code>loc: [query, offset]</code>, <br>
        - <code>msg: Input should be a valid integer, unable to parse string as an integer</code>, <br>
        - <code>type: int_parsing</code></td>
    </tr>
</table>

## USR-LIST-015: Получение списка пользователей с одновременным использованием query-параметров limit и offset

<table>
    <tr>
        <td colspan="2"><b>ID: </b>USR-LIST-015</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Получение списка пользователей с одновременным использованием query-параметров <code>limit</code> и <code>offset</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>База данных содержит не менее 6-ти пользователей</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>limit=4&offset=2</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/users</code> с указанными значениями query-параметров</td>
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
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#userslist">UsersList</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>Объект <code>meta</code> содержит: <br>
        - <code>total: &lt;фактическое количество пользователей в БД&gt;</code>, <br>
        - <code>limit: 4</code>, <br>
        - <code>offset: 2</code>.<br>
        Массив <code>data</code> содержит 4 записи. Первые 2 записи из полного списка пользователей отсутствуют</td>
    </tr>
</table>

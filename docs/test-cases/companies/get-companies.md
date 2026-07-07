# Test Cases — GET /api/companies

## CMP-LIST-001: Получение списка компаний без query-параметров

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-LIST-001</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Получение списка компаний без query-параметров</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>High</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>База данных содержит не менее 3-х компаний</td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies</code></td>
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
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#companieslist">CompaniesList</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>Массив <code>data</code> содержит первые 3 записи. <br> Объект <code>meta</code> содержит: <br>
        - <code>total: &lt;фактическое количество компаний в БД&gt;</code>, <br>
        - <code>limit: 3</code>, <br>
        - <code>offset: 0</code></td>
    </tr>
</table>

## CMP-LIST-002: Фильтрация списка компаний по статусу "ACTIVE"

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-LIST-002</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Фильтрация списка компаний по статусу <code>ACTIVE</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>High</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>База данных содержит не менее 1-й компании со статусом <code>ACTIVE</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>status=ACTIVE</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies</code> с указанным значением query-параметра</td>
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
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#companieslist">CompaniesList</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>Массив <code>data</code> не пустой. Все объекты массива имеют значение <code>company_status: ACTIVE</code></td>
    </tr>
</table>

## CMP-LIST-003: Фильтрация списка компаний по статусу "CLOSED"

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-LIST-003</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Фильтрация списка компаний по статусу <code>CLOSED</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>High</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>База данных содержит не менее 1-й компании со статусом <code>CLOSED</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>status=CLOSED</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies</code> с указанным значением query-параметра</td>
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
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#companieslist">CompaniesList</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>Массив <code>data</code> не пустой. Все объекты массива имеют значение <code>company_status: CLOSED</code></td>
    </tr>
</table>

## CMP-LIST-004: Фильтрация списка компаний по статусу "BANKRUPT"

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-LIST-004</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Фильтрация списка компаний по статусу <code>BANKRUPT</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>High</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>База данных содержит не менее 1-й компании со статусом <code>BANKRUPT</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>status=BANKRUPT</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies</code> с указанным значением query-параметра</td>
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
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#companieslist">CompaniesList</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>Массив <code>data</code> не пустой. Все объекты массива имеют значение <code>company_status: BANKRUPT</code></td>
    </tr>
</table>

## CMP-LIST-005: Проверка обработки недопустимого значения query-параметра status при получении списка компаний

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-LIST-005</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки недопустимого значения query-параметра <code>status</code> при получении списка компаний</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>High</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>status=LIQUIDATED</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies</code> с указанным значением query-параметра</td>
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
        - <code>loc: [query, status]</code>, <br>
        - <code>msg: Input should be 'ACTIVE', 'CLOSED' or 'BANKRUPT'</code>, <br>
        - <code>type: enum</code></td>
    </tr>
</table>

## CMP-LIST-006: Получение списка компаний с корректным значением query-параметра limit

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-LIST-006</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Получение списка компаний с корректным значением query-параметра <code>limit</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>High</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>База данных содержит не менее 5-ти компаний</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>limit=5</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies</code> с указанным значением query-параметра</td>
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
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#companieslist">CompaniesList</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>Массив <code>data</code> содержит ровно 5 объектов. <br> Объект <code>meta</code> содержит: <br>
        - <code>total: &lt;фактическое количество компаний в БД&gt;</code>, <br>
        - <code>limit: 5</code>, <br>
        - <code>offset: 0</code></td>
    </tr>
</table>

## CMP-LIST-007: Получение списка компаний с минимально допустимым значением query-параметра limit

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-LIST-007</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Получение списка компаний с минимально допустимым значением query-параметра <code>limit</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>High</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>База данных содержит не менее 1-й компании</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>limit=1</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies</code> с указанным значением query-параметра</td>
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
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#companieslist">CompaniesList</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>Массив <code>data</code> содержит ровно 1 объект. <br> Объект <code>meta</code> содержит: <br>
        - <code>total: &lt;фактическое количество компаний в БД&gt;</code>, <br>
        - <code>limit: 1</code>, <br>
        - <code>offset: 0</code></td>
    </tr>
</table>

## CMP-LIST-008: Проверка обработки значения limit = 0 при получении списка компаний

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-LIST-008</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки значения <code>limit = 0</code> при получении списка компаний</td>
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
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies</code> с указанным значением query-параметра</td>
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

## CMP-LIST-009: Проверка обработки отрицательного числового значения query-параметра limit при получении списка компаний

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-LIST-009</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки отрицательного числового значения query-параметра <code>limit</code> при получении списка компаний</td>
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
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies</code> с указанным значением query-параметра</td>
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

## CMP-LIST-010: Получение списка компаний с корректным значением query-параметра offset

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-LIST-010</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Получение списка компаний с корректным значением query-параметра <code>offset</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>High</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>База данных содержит более 3-х компаний</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>offset=3</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies</code> с указанным значением query-параметра</td>
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
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#companieslist">CompaniesList</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>Массив <code>data</code> не содержит первые 3 записи из полного списка компаний. <br> Объект <code>meta</code> содержит: <br>
        - <code>total: &lt;фактическое количество компаний в БД&gt;</code>, <br>
        - <code>limit: 3</code>, <br>
        - <code>offset: 3</code></td>
    </tr>
</table>

## CMP-LIST-011: Проверка обработки отрицательного числового значения query-параметра offset при получении списка компаний

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-LIST-011</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки отрицательного числового значения query-параметра <code>offset</code> при получении списка компаний</td>
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
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies</code> с указанным значением query-параметра</td>
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
        Массив <code>data</code> содержит 3 объекта, начиная с первой записи. <br> Объект <code>meta</code> содержит: <br>
        - <code>total: &lt;фактическое количество компаний в БД&gt;</code>, <br>
        - <code>limit: 3</code>, <br>
        - <code>offset: -1</code></td>
    </tr>
</table>

> _**Примечание**. Поведение при отрицательном значении <code>offset</code> не задокументировано в спецификации. До уточнения требований тест-кейс не может быть оценён как Pass/Fail. Рекомендуется согласовать с разработчиком, ожидается ли 422 или описанное фактическое поведение._

## CMP-LIST-012: Получение списка компаний при значении offset, равном или превышающем total

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-LIST-012</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Получение списка компаний при значении <code>offset</code>, равном или превышающем <code>total</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>High</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>Общее количество компаний в базе данных не превышает 99</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>offset=99</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies</code> с указанным значением query-параметра</td>
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
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#companieslist">CompaniesList</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>Массив <code>data</code> пустой (<code>[]</code>). <br> Объект <code>meta</code> содержит: <br>
        - <code>total: &lt;фактическое количество компаний в БД&gt;</code>, <br>
        - <code>limit: 3</code>, <br>
        - <code>offset: 99</code></td>
    </tr>
</table>

## CMP-LIST-013: Проверка фильтрации списка компаний по значению status в нижнем регистре

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-LIST-013</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка фильтрации списка компаний по значению <code>status</code> в нижнем регистре</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>status=active</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies</code> с указанным значением query-параметра</td>
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
        - <code>loc: [query, status]</code>, <br>
        - <code>msg: Input should be 'ACTIVE', 'CLOSED' or 'BANKRUPT'</code>, <br>
        - <code>type: enum</code></td>
    </tr>
</table>

## CMP-LIST-014: Проверка обработки числового значения query-параметра status при получении списка компаний

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-LIST-014</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки числового значения query-параметра <code>status</code> при получении списка компаний</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>status=1</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies</code> с указанным значением query-параметра</td>
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
        - <code>loc: [query, status]</code>, <br>
        - <code>msg: Input should be 'ACTIVE', 'CLOSED' or 'BANKRUPT'</code>, <br>
        - <code>type: enum</code></td>
    </tr>
</table>

## CMP-LIST-015: Проверка обработки нескольких значений query-параметра status при получении списка компаний

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-LIST-015</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки нескольких значений query-параметра <code>status</code> при получении списка компаний</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Needs Clarification</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>База данных содержит не менее 1-й компании со статусом <code>ACTIVE</code> и не менее 1-й компании со статусом <code>CLOSED</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>status=ACTIVE&status=CLOSED</code></td>
    </tr>
    <tr>
        <th rowspan="2">Шаги:</th>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies</code> с несколькими значениями указанного query-параметра</td>
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
        Массив <code>data</code> не пустой. Все объекты массива содержат только компании со статусом <code>CLOSED</code>. Компании со статусом <code>ACTIVE</code> отсутствуют</td>
    </tr>
</table>

> _**Примечание**. Передача нескольких значений параметра <code>status</code> не описана в спецификации. До уточнения требований тест-кейс не может быть оценён как Pass/Fail. Рекомендуется согласовать с разработчиком: либо сервер возвращает 422, если параметр <code>status</code> не поддерживает несколько значений, либо сервер возвращает компании по всем переданным статусам, либо сервер применяет только одно из переданных значений по заранее описанному правилу._

## CMP-LIST-016: Проверка обработки пустого значения query-параметра status при получении списка компаний

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-LIST-016</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки пустого значения query-параметра <code>status</code> при получении списка компаний</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>status=пустое значение</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies</code> с указанным значением query-параметра</td>
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
        - <code>loc: [query, status]</code>, <br>
        - <code>msg: Input should be 'ACTIVE', 'CLOSED' or 'BANKRUPT'</code>, <br>
        - <code>type: enum</code></td>
    </tr>
</table>

## CMP-LIST-017: Проверка обработки специального символа в query-параметре status при получении списка компаний

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-LIST-017</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки специального символа в query-параметре <code>status</code> при получении списка компаний</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>status=@#%</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies</code> с указанным значением query-параметра</td>
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
        - <code>loc: [query, status]</code>, <br>
        - <code>msg: Input should be 'ACTIVE', 'CLOSED' or 'BANKRUPT'</code>, <br>
        - <code>type: enum</code></td>
    </tr>
</table>

## CMP-LIST-018: Проверка обработки SQL-like значения в query-параметре status при получении списка компаний

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-LIST-018</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки SQL-like значения в query-параметре <code>status</code> при получении списка компаний</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>status=' OR '1'='1</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies</code> с указанным значением query-параметра</td>
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
        - <code>loc: [query, status]</code>, <br>
        - <code>msg: Input should be 'ACTIVE', 'CLOSED' or 'BANKRUPT'</code>, <br>
        - <code>type: enum</code><br>Ответ не содержит сведений о структуре базы данных или внутренней реализации сервиса</td>
    </tr>
</table>

## CMP-LIST-019: Проверка обработки строкового значения query-параметра limit при получении списка компаний

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-LIST-019</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки строкового значения query-параметра <code>limit</code> при получении списка компаний</td>
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
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies</code> с указанным значением query-параметра</td>
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

## CMP-LIST-020: Проверка обработки пустого значения query-параметра limit при получении списка компаний

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-LIST-020</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки пустого значения query-параметра <code>limit</code> при получении списка компаний</td>
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
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies</code> с указанным значением query-параметра</td>
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

## CMP-LIST-021: Проверка обработки дробного значения query-параметра limit при получении списка компаний

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-LIST-021</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки дробного значения query-параметра <code>limit</code> при получении списка компаний</td>
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
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies</code> с указанным значением query-параметра</td>
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

## CMP-LIST-022: Проверка обработки строкового значения query-параметра offset при получении списка компаний

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-LIST-022</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки строкового значения query-параметра <code>offset</code> при получении списка компаний</td>
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
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies</code> с указанным значением query-параметра</td>
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

## CMP-LIST-023: Проверка обработки пустого значения query-параметра offset при получении списка компаний

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-LIST-023</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки пустого значения query-параметра <code>offset</code> при получении списка компаний</td>
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
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies</code> с указанным значением query-параметра</td>
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

## CMP-LIST-024: Проверка обработки дробного значения query-параметра offset при получении списка компаний

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-LIST-024</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки дробного значения query-параметра <code>offset</code> при получении списка компаний</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>offset=4.5</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies</code> с указанным значением query-параметра</td>
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

## CMP-LIST-025: Получение списка компаний с одновременным использованием query-параметров status и limit

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-LIST-025</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Получение списка компаний с одновременным использованием query-параметров <code>status</code> и <code>limit</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>База данных содержит не менее 2-х компаний со статусом <code>ACTIVE</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>status=ACTIVE&limit=2</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies</code> с указанными значениями query-параметров</td>
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
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#companieslist">CompaniesList</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>Массив <code>data</code> содержит две записи, которые имеют значение <code>company_status: ACTIVE</code>. <br> Объект <code>meta</code> содержит: <br>
        - <code>total: &lt;фактическое количество компаний в БД&gt;</code>, <br>
        - <code>limit: 2</code>, <br>
        - <code>offset: 0</code></td>
    </tr>
</table>

## CMP-LIST-026: Получение списка компаний с одновременным использованием query-параметров status и offset

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-LIST-026</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Получение списка компаний с одновременным использованием query-параметров <code>status</code> и <code>offset</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>База данных содержит не менее 2-х компаний со статусом <code>ACTIVE</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>status=ACTIVE&offset=1</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies</code> с указанными значениями query-параметров</td>
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
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#companieslist">CompaniesList</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>Массив <code>data</code> не содержит первую запись из выборки по статусу. Все присутствующие записи имеют <code>company_status = ACTIVE</code>. <br> Объект <code>meta</code> содержит: <br>
        - <code>total: &lt;фактическое количество компаний в БД&gt;</code>, <br>
        - <code>limit: 3</code>, <br>
        - <code>offset: 1</code></td>
    </tr>
</table>

## CMP-LIST-027: Получение списка компаний с одновременным использованием query-параметров limit и offset

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-LIST-027</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Получение списка компаний с одновременным использованием query-параметров <code>limit</code> и <code>offset</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>База данных содержит не менее 3-х компаний</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>limit=2&offset=1</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies</code> с указанными значениями query-параметров</td>
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
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#companieslist">CompaniesList</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>Массив <code>data</code> содержит две записи. Первая запись из полного списка компаний отсутствует. <br> Объект <code>meta</code> содержит: <br>
        - <code>total: &lt;фактическое количество компаний в БД&gt;</code>, <br>
        - <code>limit: 2</code>, <br>
        - <code>offset: 1</code></td>
    </tr>
</table>

## CMP-LIST-028: Получение списка компаний с одновременным использованием query-параметров status, limit и offset

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-LIST-028</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Получение списка компаний с одновременным использованием query-параметров <code>status</code>, <code>limit</code> и <code>offset</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>База данных содержит не менее 3-х компаний со статусом <code>ACTIVE</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>status=ACTIVE&limit=2&offset=1</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies</code> с указанными значениями query-параметров</td>
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
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#companieslist">CompaniesList</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>Массив <code>data</code> содержит две записи. Первая запись из выборки по статусу отсутствует. Все присутствующие записи имеют <code>company_status = ACTIVE</code>. <br> Объект <code>meta</code> содержит: <br>
        - <code>total: &lt;фактическое количество компаний в БД&gt;</code>, <br>
        - <code>limit: 2</code>, <br>
        - <code>offset: 1</code></td>
    </tr>
</table>

## CMP-LIST-029: Получение списка компаний при отправке запроса по HTTP-протоколу

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-LIST-029</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Получение списка компаний при отправке запроса по HTTP-протоколу</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Low</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>http://restapi.tech/api/companies</code></td>
        <td>Статус-код: <code>301 Moved Permanently</code></td>
    </tr>
    <tr>
        <td>2. Проверить время ответа сервера</td>
        <td>Время ответа сервера ≤ 500 ms</td>
    </tr>
    <tr>
        <td>3. Проверить заголовки ответа</td>
        <td><code>Content-Type: text/html</code><br><code>Location: https://restapi.tech/api/companies</code></td>
    </tr>
</table>

# Test Cases — GET /api/companies/{company_id}

## CMP-ID-001: Получение информации о существующей компании с заголовком Accept-Language: EN

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-ID-001</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Получение информации о существующей компании с заголовком <code>Accept-Language: EN</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>High</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>В базе данных существует компания с <code>company_id = {{existingCompanyId}}</code>, имеющая перевод для выбранного языка</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b>
        <ul>
            <li><code>company_id = {{existingCompanyId}}</code></li>
            <li><code>Accept-Language: EN</code></li>
        </ul>
        </td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies/{{existingCompanyId}}</code> c указанным значением заголовка <code>Accept-Language</code></td>
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
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#companywithallowedlanguage">CompanyWithAllowedLanguage</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>Значение <code>company_id</code> совпадает с переданным в URI.<br>Ключ <code>description</code> содержит непустую строку на языке, указанном в заголовке <code>Accept-Language</code></td>
    </tr>
</table>

## CMP-ID-002: Получение информации о существующей компании без заголовка Accept-Language

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-ID-002</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Получение информации о существующей компании без заголовка <code>Accept-Language</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>High</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>В базе данных существует компания с <code>company_id = {{existingCompanyId}}</code>, имеющая переводы в <code>description_lang</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>company_id = {{existingCompanyId}}</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies/{{existingCompanyId}}</code> без заголовка <code>Accept-Language</code></td>
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
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#companywithnonallowedlanguage">CompanyWithNonAllowedLanguage</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>Значение <code>company_id</code> совпадает с переданным в URI.<br>Массив <code>description_lang</code> не пустой и содержит не менее 1-го объекта с заполненными <code>translation_lang</code> и <code>translation</code></td>
    </tr>
</table>

## CMP-ID-003: Проверка обработки несуществующего значения параметра пути company_id при получении информации о компании

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-ID-003</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки несуществующего значения параметра пути <code>company_id</code> при получении информации о компании</td>
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
        <td colspan="2"><b>Тестовые данные: </b><code>company_id = {{nonexistentCompanyId}}</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies/{{nonexistentCompanyId}}</code></td>
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

## CMP-ID-004: Получение информации о компании с заголовком Accept-Language: RU

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-ID-004</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Получение информации о компании с заголовком <code>Accept-Language: RU</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>High</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>В базе данных существует компания с <code>company_id = {{existingCompanyId}}</code>, имеющая перевод для выбранного языка</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b>
        <ul>
            <li><code>company_id = {{existingCompanyId}}</code></li>
            <li><code>Accept-Language: RU</code></li>
        </ul>
        </td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies/{{existingCompanyId}}</code> c указанным значением заголовка <code>Accept-Language</code></td>
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
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#companywithallowedlanguage">CompanyWithAllowedLanguage</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>Значение <code>company_id</code> совпадает с переданным в URI.<br>Ключ <code>description</code> содержит непустую строку на языке, указанном в заголовке <code>Accept-Language</code></td>
    </tr>
</table>

## CMP-ID-005: Получение информации о компании с заголовком Accept-Language: PL

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-ID-005</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Получение информации о компании с заголовком <code>Accept-Language: PL</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>High</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>В базе данных существует компания с <code>company_id = {{existingCompanyId}}</code>, имеющая перевод для выбранного языка</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b>
        <ul>
            <li><code>company_id = {{existingCompanyId}}</code></li>
            <li><code>Accept-Language: PL</code></li>
        </ul>
        </td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies/{{existingCompanyId}}</code> c указанным значением заголовка <code>Accept-Language</code></td>
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
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#companywithallowedlanguage">CompanyWithAllowedLanguage</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>Значение <code>company_id</code> совпадает с переданным в URI.<br>Ключ <code>description</code> содержит непустую строку на языке, указанном в заголовке <code>Accept-Language</code></td>
    </tr>
</table>

## CMP-ID-006: Проверка обработки значения company_id = 0 при получении информации о компании

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-ID-006</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки значения <code>company_id = 0</code> при получении информации о компании</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>company_id = 0</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies/{company_id}</code><br> c указанным значением path-параметра</td>
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

## CMP-ID-007: Проверка обработки отрицательного числового значения параметра пути company_id при получении информации о компании

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-ID-007</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки отрицательного числового значения параметра пути <code>company_id</code> при получении информации о компании</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>company_id = -1</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies/{company_id}</code><br> c указанным значением path-параметра</td>
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

## CMP-ID-008: Проверка обработки строкового значения параметра пути company_id при получении информации о компании

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-ID-008</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки строкового значения параметра пути <code>company_id</code> при получении информации о компании</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>company_id = one</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies/{company_id}</code> с указанным значением path-параметра</td>
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
        - <code>loc: [path, company_id]</code>, <br>
        - <code>msg: Input should be a valid integer, unable to parse string as an integer</code>, <br>
        - <code>type: int_parsing</code></td>
    </tr>
</table>

## CMP-ID-009: Проверка обработки дробного значения параметра пути company_id при получении информации о компании

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-ID-009</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки дробного значения параметра пути <code>company_id</code> при получении информации о компании</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b><code>company_id = 1.5</code></td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies/{company_id}</code> с указанным значением path-параметра</td>
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
        - <code>loc: [path, company_id]</code>, <br>
        - <code>msg: Input should be a valid integer, unable to parse string as an integer</code>, <br>
        - <code>type: int_parsing</code></td>
    </tr>
</table>

## CMP-ID-010: Проверка обработки неподдерживаемого значения заголовка Accept-Language при получении информации о компании

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-ID-010</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки неподдерживаемого значения заголовка <code>Accept-Language</code> при получении информации о компании</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>В базе данных существует компания с <code>company_id = {{existingCompanyId}}</code>, имеющая переводы в <code>description_lang</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b>
        <ul>
            <li><code>company_id = {{existingCompanyId}}</code></li>
            <li><code>Accept-Language: DE</code></li>
        </ul>
        </td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies/{{existingCompanyId}}</code> c указанным значением заголовка <code>Accept-Language</code></td>
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
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#companywithnonallowedlanguage">CompanyWithNonAllowedLanguage</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>Значение <code>company_id</code> совпадает с переданным в URI.<br>Массив <code>description_lang</code> не пустой и содержит не менее 1-го объекта с заполненными <code>translation_lang</code> и <code>translation</code></td>
    </tr>
</table>

## CMP-ID-011: Проверка обработки пустого значения заголовка Accept-Language при получении информации о компании

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-ID-011</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки пустого значения заголовка <code>Accept-Language</code> при получении информации о компании</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>В базе данных существует компания с <code>company_id = {{existingCompanyId}}</code>, имеющая переводы в <code>description_lang</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b>
        <ul>
            <li><code>company_id = {{existingCompanyId}}</code></li>
            <li><code>Accept-Language: пустое значение</code></li>
        </ul>
        </td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies/{{existingCompanyId}}</code> c указанным значением заголовка <code>Accept-Language</code></td>
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
        <td>Тело ответа соответствует JSON Schema <a href="https://github.com/failytale/api-testing-project/blob/main/docs/schemas/response-schemas.md#companywithnonallowedlanguage">CompanyWithNonAllowedLanguage</a></td>
    </tr>
    <tr>
        <td>5. Проверить значения полей ответа</td>
        <td>Значение <code>company_id</code> совпадает с переданным в URI.<br>Массив <code>description_lang</code> не пустой и содержит не менее 1-го объекта с заполненными <code>translation_lang</code> и <code>translation</code></td>
    </tr>
</table>

## CMP-ID-012: Проверка обработки нескольких поддерживаемых значений заголовка Accept-Language при получении информации о компании

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-ID-012</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки нескольких поддерживаемых значений заголовка <code>Accept-Language</code> при получении информации о компании</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Needs Clarification</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>В базе данных существует компания с <code>company_id = {{existingCompanyId}}</code>, имеющая переводы в <code>description_lang</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b>
        <ul>
            <li><code>company_id = {{existingCompanyId}}</code></li>
            <li><code>Accept-Language: RU,EN</code></li>
        </ul>
        </td>
    </tr>
    <tr>
        <th rowspan="2">Шаги:</th>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies/{{existingCompanyId}}</code> c указанным значением заголовка <code>Accept-Language</code></td>
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
        Сервер возвращает тело ответа, соответствующее поведению для неподдерживаемого или отсутствующего значения <code>Accept-Language</code></td>
    </tr>
</table>

> _**Примечание**. Поведение при передаче нескольких значений заголовка <code>Accept-Language</code> не задокументировано в спецификации. До уточнения требований тест-кейс не может быть оценён как Pass/Fail. Рекомендуется согласовать с разработчиком: либо сервер выбирает один из языков по приоритету, либо сервер возвращает список переводов в <code>description_lang</code>, либо сервер возвращает ошибку валидации, если несколько значений не поддерживаются._

## CMP-ID-013: Проверка обработки поддерживаемого значения заголовка Accept-Language в нижнем регистре при получении информации о компании

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-ID-013</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка обработки поддерживаемого значения заголовка <code>Accept-Language</code> в нижнем регистре при получении информации о компании</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Medium</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Needs Clarification</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>В базе данных существует компания с <code>company_id = {{existingCompanyId}}</code>, имеющая перевод для выбранного языка</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b>
        <ul>
            <li><code>company_id = {{existingCompanyId}}</code></li>
            <li><code>Accept-Language: ru</code></li>
        </ul>
        </td>
    </tr>
    <tr>
        <th rowspan="2">Шаги:</th>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies/{{existingCompanyId}}</code> c указанным значением заголовка <code>Accept-Language</code></td>
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
        Сервер возвращает тело ответа, соответствующее поведению для неподдерживаемого или отсутствующего значения <code>Accept-Language</code></td>
    </tr>
</table>

> _**Примечание**. Поведение при передаче поддерживаемого значения <code>Accept-Language</code> в нижнем регистре не описано в спецификации. До уточнения требований тест-кейс не может быть оценён как Pass/Fail. Рекомендуется согласовать с разработчиком: должен ли сервер обрабатывать значения <code>Accept-Language</code> без учёта регистра, либо значения должны передаваться в предусмотренном формате и обрабатываться как неподдерживаемые при его нарушении._

## CMP-ID-014: Проверка отсутствия изменения состояния при повторном GET-запросе с одинаковыми параметрами при получении информации о компании

<table>
    <tr>
        <td colspan="2"><b>ID: </b>CMP-ID-014</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка отсутствия изменения состояния при повторном GET-запросе с одинаковыми параметрами при получении информации о компании</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>Low</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>В базе данных существует компания с <code>company_id = {{existingCompanyId}}</code>, имеющая перевод для выбранного языка</td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b>
        <ul>
            <li><code>company_id = {{existingCompanyId}}</code></li>
            <li><code>Accept-Language: UA</code></li>
        </ul>
        </td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/companies/{{existingCompanyId}}</code> c указанным значением заголовка <code>Accept-Language</code></td>
        <td>Статус-код: <code>200 OK</code>.<br>Тело ответа сохранено как <code>Response 1</code></td>
    </tr>
    <tr>
        <td>2. Повторно отправить идентичный GET-запрос на <code>{{baseUrl}}/api/companies/{{existingCompanyId}}</code> c указанным значением заголовка <code>Accept-Language</code></td>
        <td>Статус-код: <code>200 OK</code>.<br>Тело ответа сохранено как <code>Response 2</code></td>
    </tr>
    <tr>
        <td>3. Сравнить <code>Response 1</code> и <code>Response 2</code></td>
        <td>Тела ответов <code>Response 1</code> и <code>Response 2</code> идентичны.<br>Совпадают значения: <code>company_id</code>, <code>company_name</code>, <code>company_address</code>, <code>company_status</code>, <code>description</code></td>
    </tr>
</table>

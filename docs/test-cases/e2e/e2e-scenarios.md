# Test Cases — End-to-End Scenarios

## E2E-001: Проверка полного жизненного цикла пользователя: создание, получение, обновление с привязкой к другой активной компании, повторное получение, удаление и проверка недоступности

<table>
    <tr>
        <td colspan="2"><b>ID: </b>E2E-001</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка полного жизненного цикла пользователя: создание, получение, обновление с привязкой к другой активной компании, повторное получение, удаление и проверка недоступности</td>
    </tr>
    <tr>
        <td colspan="2"><b>Приоритет: </b>High</td>
    </tr>
    <tr>
        <td colspan="2"><b>Статус: </b>Pass</td>
    </tr>
    <tr>
        <td colspan="2"><b>Предусловие: </b>В базе данных существуют две активные компании с <code>company_id = {{activeCompanyId}}</code><br> и <code>company_id = {{activeCompanyId2}}</code></td>
    </tr>
    <tr>
        <td colspan="2"><b>Тестовые данные: </b>
        <ol>
            <li>POST Request Body: <pre><code>{
  "first_name": "Elliot", 
  "last_name": "Alderson",
  "company_id": {{activeCompanyId}}
}</code></pre></li>
            <li>PUT Request Body: <pre><code>{
  "first_name": "Angela", 
  "last_name": "Moss",
  "company_id": {{activeCompanyId2}}
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
        <td>1. Отправить POST-запрос на <code>{{baseUrl}}/api/users</code> с телом запроса</td>
        <td>Статус-код: <code>201 Created</code></td>
    </tr>
    <tr>
        <td>2. Сохранить <code>user_id</code> из тела ответа как <code>{{createdUserId}}</code></td>
        <td>Значение <code>user_id</code> сохранено как <code>{{createdUserId}}</code></td>
    </tr>
    <tr>
        <td>3. Отправить GET-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code></td>
        <td>Статус-код: <code>200 OK</code></td>
    </tr>
    <tr>
        <td>4. Проверить тело ответа</td>
        <td>Данные совпадают с переданными в POST-запросе:<br>
        - <code>first_name: Elliot</code>,<br>
        - <code>last_name: Alderson</code>,<br>
        - <code>company_id: {{activeCompanyId}}</code>,<br>
        - <code>user_id: {{createdUserId}}</code></td>
    </tr>
    <tr>
        <td>5. Отправить PUT-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code> с телом запроса</td>
        <td>Статус-код: <code>200 OK</code></td>
    </tr>
    <tr>
        <td>6. Отправить повторный GET-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code></td>
        <td>Статус-код: <code>200 OK</code></td>
    </tr>
    <tr>
        <td>7. Проверить тело ответа</td>
        <td>Данные успешно обновлены и совпадают с переданными в PUT-запросе:<br>
        - <code>first_name: Angela</code>,<br>
        - <code>last_name: Moss</code>,<br>
        - <code>company_id: {{activeCompanyId2}}</code>,<br>
        - <code>user_id: {{createdUserId}}</code></td>
    </tr>
    <tr>
        <td>8. Отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code></td>
        <td>Статус-код: <code>202 Accepted</code></td>
    </tr>
    <tr>
        <td>9. Отправить повторный GET-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code></td>
        <td>Статус-код: <code>404 Not Found</code></td>
    </tr>
    <tr>
        <td>10. Проверить тело ответа</td>
        <td>Пользователь недоступен после удаления.<br>Объект <code>detail</code> содержит:<br>
        - <code>reason: User with requested id: &lt;createdUserId&gt; is absent</code></td>
    </tr>
</table>

## E2E-002: Проверка появления пользователя в списке после создания и отсутствия в списке после удаления

<table>
    <tr>
        <td colspan="2"><b>ID: </b>E2E-002</td>
    </tr>
    <tr>
        <td colspan="2"><b>Название: </b>Проверка появления пользователя в списке после создания и отсутствия в списке после удаления</td>
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
        <td colspan="2"><b>Тестовые данные: </b>
        <ol>
            <li>POST Request Body: <pre><code>{
  "first_name": "Elliot", 
  "last_name": "Alderson",
  "company_id": {{activeCompanyId}}
}</code></pre></li>
            <li><code>offset = {{initialTotal}}</code></li>
            <li><code>user_id = {{createdUserId}}</code></li>
        </ol>
        </td>
    </tr>
    <tr>
        <th>Шаги</th>
        <th>Ожидаемый результат</th>
    </tr>
    <tr>
        <td>1. Отправить GET-запрос на <code>{{baseUrl}}/api/users</code> без query-параметров</td>
        <td>Статус-код: <code>200 OK</code></td>
    </tr>
    <tr>
        <td>2. Сохранить  значение <code>total</code> объекта <code>meta</code> из тела ответа как <code>{{initialTotal}}</code></td>
        <td>Значение <code>total</code> сохранено как <code>{{initialTotal}}</code></td>
    </tr>
    <tr>
        <td>3. Отправить POST-запрос на <code>{{baseUrl}}/api/users</code> с телом запроса</td>
        <td>Статус-код: <code>201 Created</code></td>
    </tr>
    <tr>
        <td>4. Сохранить <code>user_id</code> из тела ответа как <code>{{createdUserId}}</code></td>
        <td>Значение <code>user_id</code> сохранено как <code>{{createdUserId}}</code></td>
    </tr>
    <tr>
        <td>5. Отправить GET-запрос на <code>{{baseUrl}}/api/users</code> с указанным значением query-параметра</td>
        <td>Статус-код: <code>200 OK</code></td>
    </tr>
    <tr>
        <td>6. Проверить тело ответа</td>
        <td>Объект <code>meta</code> содержит: <br>
        - <code>total: {{initialTotal}} + 1</code>,<br>
        - <code>limit: 3</code>,<br>
        - <code>offset: {{initialTotal}}</code>,<br>
        В массиве <code>data</code> присутствует пользователь с <code>user_id: {{createdUserId}}</code></td>
    </tr>
    <tr>
        <td>7. Отправить DELETE-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code></td>
        <td>Статус-код: <code>202 Accepted</code></td>
    </tr>
    <tr>
        <td>8. Отправить GET-запрос на <code>{{baseUrl}}/api/users/{{createdUserId}}</code></td>
        <td>Статус-код: <code>404 Not Found</code></td>
    </tr>
    <tr>
        <td>9. Проверить тело ответа</td>
        <td>Пользователь недоступен после удаления.<br>Объект <code>detail</code> содержит:<br>
        - <code>reason: User with requested id: &lt;createdUserId&gt; is absent</code></td>
    </tr>
</table>

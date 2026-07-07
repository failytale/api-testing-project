# API Checklist

## 1. GET /api/companies

<table>
  <tr>
        <th>ID</th>
        <th>Название</th>
        <th>Статус</th>
    </tr>
    <tr>
      <td align="center">1.1</td>
      <td>Получение списка компаний без query-параметров</td>
      <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.2</td>
        <td>Фильтрация списка компаний по статусу <code>ACTIVE</code></td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.3</td>
        <td>Фильтрация списка компаний по статусу <code>CLOSED</code></td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.4</td>
        <td>Фильтрация списка компаний по статусу <code>BANKRUPT</code></td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.5</td>
        <td>Проверка обработки недопустимого значения query-параметра <code>status</code> при получении списка компаний</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.6</td>
        <td>Получение списка компаний с корректным значением query-параметра <code>limit</code></td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.7</td>
        <td>Получение списка компаний с минимально допустимым значением query-параметра <code>limit</code></td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.8</td>
        <td>Проверка обработки значения <code>limit = 0</code> при получении списка компаний</td>
        <td align="center">Fail</td>
    </tr>
    <tr>
        <td align="center">1.9</td>
        <td>Проверка обработки отрицательного числового значения query-параметра <code>limit</code> при получении списка компаний</td>
        <td align="center">Fail</td>
    </tr>
    <tr>
        <td align="center">1.10</td>
        <td>Получение списка компаний с корректным значением query-параметра <code>offset</code></td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.11</td>
        <td>Проверка обработки отрицательного числового значения query-параметра <code>offset</code> при получении списка компаний</td>
        <td align="center">Needs clarification</td>
    </tr>
    <tr>
        <td align="center">1.12</td>
        <td>Получение списка компаний при значении <code>offset</code>, равном или превышающем <code>total</code></td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.13</td>
        <td>Проверка фильтрации списка компаний по значению <code>status</code> в нижнем регистре</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.14</td>
        <td>Проверка обработки числового значения query-параметра <code>status</code> при получении списка компаний</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.15</td>
        <td>Проверка обработки нескольких значений query-параметра <code>status</code> при получении списка компаний</td>
        <td align="center">Needs clarification</td>
    </tr>
    <tr>
        <td align="center">1.16</td>
        <td>Проверка обработки пустого значения query-параметра <code>status</code> при получении списка компаний</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.17</td>
        <td>Проверка обработки специального символа в query-параметре <code>status</code> при получении списка компаний</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.18</td>
        <td>Проверка обработки SQL-like значения в query-параметре <code>status</code> при получении списка компаний</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.19</td>
        <td>Проверка обработки строкового значения query-параметра <code>limit</code> при получении списка компаний</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.20</td>
        <td>Проверка обработки пустого значения query-параметра <code>limit</code> при получении списка компаний</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.21</td>
        <td>Проверка обработки дробного значения query-параметра <code>limit</code> при получении списка компаний</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.22</td>
        <td>Проверка обработки строкового значения query-параметра <code>offset</code> при получении списка компаний</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.23</td>
        <td>Проверка обработки пустого значения query-параметра <code>offset</code> при получении списка компаний</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.24</td>
        <td>Проверка обработки дробного значения query-параметра <code>offset</code> при получении списка компаний</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.25</td>
        <td>Получение списка компаний с одновременным использованием query-параметров <code>status</code> и <code>limit</code></td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.26</td>
        <td>Получение списка компаний с одновременным использованием query-параметров <code>status</code> и <code>offset</code></td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.27</td>
        <td>Получение списка компаний с одновременным использованием query-параметров <code>limit</code> и <code>offset</code></td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.28</td>
        <td>Получение списка компаний с одновременным использованием query-параметров <code>status</code>, <code>limit</code> и <code>offset</code></td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.29</td>
        <td>Получение списка компаний при отправке запроса по HTTP-протоколу</td>
        <td align="center">Pass</td>
    </tr>
</table>

## 2. GET /api/companies/{company_id}

<table>
  <tr>
        <th>ID</th>
        <th>Название</th>
        <th>Статус</th>
    </tr>
    <tr>
      <td align="center">2.1</td>
      <td>Получение информации о существующей компании с заголовком <code>Accept-Language: EN</code></td>
      <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">2.2</td>
        <td>Получение информации о существующей компании без заголовка <code>Accept-Language</code></td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">2.3</td>
        <td>Проверка обработки несуществующего значения параметра пути <code>company_id</code> при получении информации о компании</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">2.4</td>
        <td>Получение информации о компании с заголовком <code>Accept-Language: RU</code></td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">2.5</td>
        <td>Получение информации о компании с заголовком <code>Accept-Language: PL</code></td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">2.6</td>
        <td>Проверка обработки значения <code>company_id = 0</code> при получении информации о компании</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">2.7</td>
        <td>Проверка обработки отрицательного числового значения параметра пути <code>company_id</code> при получении информации о компании</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">2.8</td>
        <td>Проверка обработки строкового значения параметра пути <code>company_id</code> при получении информации о компании</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">2.9</td>
        <td>Проверка обработки дробного значения параметра пути <code>company_id</code> при получении информации о компании</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">2.10</td>
        <td>Проверка обработки неподдерживаемого значения заголовка <code>Accept-Language</code> при получении информации о компании</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">2.11</td>
        <td>Проверка обработки пустого значения заголовка <code>Accept-Language</code> при получении информации о компании</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">2.12</td>
        <td>Проверка обработки нескольких поддерживаемых значений заголовка <code>Accept-Language</code> при получении информации о компании</td>
        <td align="center">Needs clarification</td>
    </tr>
    <tr>
        <td align="center">2.13</td>
        <td>Проверка обработки поддерживаемого значения заголовка <code>Accept-Language</code> в нижнем регистре при получении информации о компании</td>
        <td align="center">Needs clarification</td>
    </tr>
    <tr>
        <td align="center">2.14</td>
        <td>Проверка отсутствия изменения состояния при повторном GET-запросе с одинаковыми параметрами при получении информации о компании</td>
        <td align="center">Pass</td>
    </tr>
</table>

## 3. GET /api/users

<table>
  <tr>
        <th>ID</th>
        <th>Название</th>
        <th>Статус</th>
    </tr>
    <tr>
      <td align="center">3.1</td>
      <td>Получение списка пользователей без query-параметров</td>
      <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">3.2</td>
        <td>Получение списка пользователей с корректным значением query-параметра <code>limit</code></td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">3.3</td>
        <td>Получение списка пользователей с минимально допустимым значением query-параметра <code>limit</code></td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">3.4</td>
        <td>Проверка обработки значения <code>limit = 0</code> при получении списка пользователей</td>
        <td align="center">Fail</td>
    </tr>
    <tr>
        <td align="center">3.5</td>
        <td>Проверка обработки отрицательного числового значения query-параметра <code>limit</code> при получении списка пользователей</td>
        <td align="center">Fail</td>
    </tr>
    <tr>
        <td align="center">3.6</td>
        <td>Получение списка пользователей с корректным значением query-параметра <code>offset</code></td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">3.7</td>
        <td>Получение списка пользователей при значении <code>offset</code>, равном или превышающем <code>total</code></td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">3.8</td>
        <td>Проверка обработки отрицательного числового значения query-параметра <code>offset</code> при получении списка пользователей</td>
        <td align="center">Needs clarification</td>
    </tr>
    <tr>
        <td align="center">3.9</td>
        <td>Проверка обработки строкового значения query-параметра <code>limit</code> при получении списка пользователей</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">3.10</td>
        <td>Проверка обработки пустого значения query-параметра <code>limit</code> при получении списка пользователей</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">3.11</td>
        <td>Проверка обработки дробного значения query-параметра <code>limit</code> при получении списка пользователей</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">3.12</td>
        <td>Проверка обработки строкового значения query-параметра <code>offset</code> при получении списка пользователей</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">3.13</td>
        <td>Проверка обработки пустого значения query-параметра <code>offset</code> при получении списка пользователей</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">3.14</td>
        <td>Проверка обработки дробного значения query-параметра <code>offset</code> при получении списка пользователей</td>
        <td align="center">Pass</td>
    </tr>
      <tr>
        <td align="center">3.15</td>
        <td>Получение списка пользователей с одновременным использованием query-параметров <code>limit</code> и <code>offset</code></td>
        <td align="center">Pass</td>
    </tr>
</table>

## 4. GET /api/users/{user_id}

<table>
  <tr>
        <th>ID</th>
        <th>Название</th>
        <th>Статус</th>
    </tr>
    <tr>
      <td align="center">4.1</td>
      <td>Получение информации о существующем пользователе по <code>user_id</code></td>
      <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">4.2</td>
        <td>Проверка обработки несуществующего значения параметра пути <code>user_id</code> при получении информации о пользователе</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">4.3</td>
        <td>Проверка обработки значения <code>user_id = 0</code> при получении информации о пользователе</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">4.4</td>
        <td>Проверка обработки отрицательного числового значения параметра пути <code>user_id</code> при получении информации о пользователе</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">4.5</td>
        <td>Проверка обработки строкового значения параметра пути <code>user_id</code> при получении информации о пользователе</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">4.6</td>
        <td>Проверка обработки дробного значения параметра пути <code>user_id</code> при получении информации о пользователе</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">4.7</td>
        <td>Проверка отсутствия изменения состояния при повторном GET-запросе с одинаковым <code>user_id</code> при получении информации о пользователе</td>
        <td align="center">Pass</td>
    </tr>
</table>

## 5. POST /api/users

<table>
  <tr>
        <th>ID</th>
        <th>Название</th>
        <th>Статус</th>
    </tr>
    <tr>
      <td align="center">5.1</td>
      <td>Создание пользователя с валидными значениями всех полей</td>
      <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">5.2</td>
        <td>Создание пользователя со значением <code>first_name = null</code></td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">5.3</td>
        <td>Проверка обработки значения <code>last_name = null</code> при создании пользователя</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">5.4</td>
        <td>Создание пользователя со значением <code>company_id = null</code></td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">5.5</td>
        <td>Проверка обработки запроса без обязательного поля <code>last_name</code> при создании пользователя</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">5.6</td>
        <td>Проверка обработки попытки создания пользователя с привязкой к компании со статусом <code>CLOSED</code></td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">5.7</td>
        <td>Проверка обработки попытки создания пользователя с привязкой к компании со статусом <code>BANKRUPT</code></td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">5.8</td>
        <td>Проверка обработки несуществующего значения поля <code>company_id</code> при создании пользователя</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">5.9</td>
        <td>Проверка обработки попытки создания пользователя без тела запроса</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">5.10</td>
        <td>Создание двух пользователей с идентичными данными</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">5.11</td>
        <td>Создание пользователя без необязательных полей <code>first_name</code> и <code>company_id</code></td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">5.12</td>
        <td>Проверка обработки значения <code>company_id = 0</code> при создании пользователя</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">5.13</td>
        <td>Проверка обработки отрицательного числового значения поля <code>company_id</code> при создании пользователя</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">5.14</td>
        <td>Проверка обработки строкового значения поля <code>company_id</code> при создании пользователя</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">5.15</td>
        <td>Проверка обработки дробного значения поля <code>company_id</code> при создании пользователя</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">5.16</td>
        <td>Проверка обработки числового значения поля <code>first_name</code> при создании пользователя</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">5.17</td>
        <td>Проверка обработки числового значения поля <code>last_name</code> при создании пользователя</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">5.18</td>
        <td>Проверка обработки невалидного JSON в теле запроса при создании пользователя</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">5.19</td>
        <td>Проверка обработки запроса с заголовком <code>Content-Type: application/xml</code> при создании пользователя</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">5.20</td>
        <td>Проверка обработки запроса без заголовка <code>Content-Type</code> при создании пользователя</td>
        <td align="center">Needs clarification</td>
    </tr>
    <tr>
        <td align="center">5.21</td>
        <td>Проверка обработки дополнительного поля в теле запроса при создании пользователя</td>
        <td align="center">Pass</td>
    </tr>
</table>

## 6. PUT /api/users/{user_id}

<table>
  <tr>
        <th>ID</th>
        <th>Название</th>
        <th>Статус</th>
    </tr>
    <tr>
      <td align="center">6.1</td>
      <td>Обновление пользователя с валидными значениями всех полей</td>
      <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.2</td>
        <td>Обновление пользователя со значением <code>first_name = null</code></td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.3</td>
        <td>Обновление пользователя со значением <code>company_id = null</code></td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.4</td>
        <td>Проверка обработки значения <code>last_name = null</code> при обновлении пользователя</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.5</td>
        <td>Проверка обработки попытки обновления пользователя с привязкой к компании со статусом <code>CLOSED</code></td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.6</td>
        <td>Проверка обработки попытки обновления пользователя с привязкой к компании со статусом <code>BANKRUPT</code></td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.7</td>
        <td>Проверка обработки попытки обновления несуществующего пользователя</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.8</td>
        <td>Проверка обработки попытки обновления пользователя с несуществующим значением <code>company_id</code></td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.9</td>
        <td>Проверка обработки запроса на обновление без обязательного поля <code>last_name</code></td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.10</td>
        <td>Проверка обработки запроса на обновление пользователя без тела запроса</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.11</td>
        <td>Проверка идемпотентности повторного PUT-запроса с одинаковым телом запроса</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.12</td>
        <td>Проверка обработки строкового значения параметра пути <code>user_id</code> при обновлении пользователя</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.13</td>
        <td>Обновление пользователя без необязательных полей <code>first_name</code> и <code>company_id</code></td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.14</td>
        <td>Проверка обработки числового значения поля <code>first_name</code> при обновлении пользователя</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.15</td>
        <td>Проверка обработки числового значения поля <code>last_name</code> при обновлении пользователя</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.16</td>
        <td>Проверка обработки значения <code>user_id = 0</code> при обновлении пользователя</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.17</td>
        <td>Проверка обработки отрицательного числового значения параметра пути <code>user_id</code> при обновлении пользователя</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.18</td>
        <td>Проверка обработки дробного значения параметра пути <code>user_id</code> при обновлении пользователя</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.19</td>
        <td>Проверка обработки значения <code>company_id = 0</code> при обновлении пользователя</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.20</td>
        <td>Проверка обработки отрицательного числового значения поля <code>company_id</code> при обновлении пользователя</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.21</td>
        <td>Проверка обработки строкового значения поля <code>company_id</code> при обновлении пользователя</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.22</td>
        <td>Проверка обработки дробного значения поля <code>company_id</code> при обновлении пользователя</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.23</td>
        <td>Проверка обработки запроса на обновление без заголовка <code>Content-Type</code></td>
        <td align="center">Needs clarification</td>
    </tr>
    <tr>
        <td align="center">6.24</td>
        <td>Проверка обработки запроса на обновление с заголовком <code>Content-Type: application/xml</code></td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.25</td>
        <td>Проверка обработки невалидного JSON в теле запроса при обновлении пользователя</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.26</td>
        <td>Проверка обработки дополнительного поля в теле запроса при обновлении пользователя</td>
        <td align="center">Pass</td>
    </tr>
</table>

## 7. DELETE /api/users/{user_id}

<table>
  <tr>
        <th>ID</th>
        <th>Название</th>
        <th>Статус</th>
    </tr>
    <tr>
      <td align="center">7.1</td>
      <td>Удаление существующего пользователя по <code>user_id</code></td>
      <td align="center">Fail</td>
    </tr>
    <tr>
        <td align="center">7.2</td>
        <td>Проверка повторного удаления ранее удалённого пользователя</td>
        <td align="center">Fail</td>
    </tr>
    <tr>
        <td align="center">7.3</td>
        <td>Проверка удаления пользователя с несуществующим значением <code>user_id</code></td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">7.4</td>
        <td>Проверка обработки строкового значения параметра пути <code>user_id</code> при удалении пользователя</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">7.5</td>
        <td>Проверка обработки значения <code>user_id = 0</code> при удалении пользователя</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">7.6</td>
        <td>Проверка обработки отрицательного числового значения параметра пути <code>user_id</code> при удалении пользователя</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">7.7</td>
        <td>Проверка обработки дробного значения параметра пути <code>user_id</code> при удалении пользователя</td>
        <td align="center">Pass</td>
    </tr>
</table>

## 8. End-to-End сценарии
<table>
  <tr>
        <th>ID</th>
        <th>Название</th>
        <th>Статус</th>
    </tr>
    <tr>
      <td align="center">8.1</td>
      <td>Проверка полного жизненного цикла пользователя: создание, получение, обновление с привязкой к другой активной компании, повторное получение, удаление и проверка недоступности</td>
      <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">8.2</td>
        <td>Проверка появления пользователя в списке после создания и отсутствия в списке после удаления</td>
        <td align="center">Pass</td>
    </tr>
</table>

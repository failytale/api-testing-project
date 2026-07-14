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
      <td>Без query-параметров</td>
      <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.2</td>
        <td>status = ACTIVE</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.3</td>
        <td>status = CLOSED</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.4</td>
        <td>status = BANKRUPT</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.5</td>
        <td>status = недопустимое значение</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.6</td>
        <td>limit = корректное значение</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.7</td>
        <td>limit = минимально допустимое значение</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.8</td>
        <td>limit = 0</td>
        <td align="center">Fail</td>
    </tr>
    <tr>
        <td align="center">1.9</td>
        <td>limit = отрицательное число</td>
        <td align="center">Fail</td>
    </tr>
    <tr>
        <td align="center">1.10</td>
        <td>offset = корректное значение</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.11</td>
        <td>offset = отрицательное число</td>
        <td align="center">Needs clarification</td>
    </tr>
    <tr>
        <td align="center">1.12</td>
        <td>offset ≥ total</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.13</td>
        <td>status в нижнем регистре</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.14</td>
        <td>status = числовое значение</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.15</td>
        <td>status = несколько значений</td>
        <td align="center">Needs clarification</td>
    </tr>
    <tr>
        <td align="center">1.16</td>
        <td>status = пустое значение</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.17</td>
        <td>status = спецсимвол</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.18</td>
        <td>status = SQL-like значение</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.19</td>
        <td>limit = строка</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.20</td>
        <td>limit = пустое значение</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.21</td>
        <td>limit = дробное число</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.22</td>
        <td>offset = строка</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.23</td>
        <td>offset = пустое значение</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.24</td>
        <td>offset = дробное число</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.25</td>
        <td>status + limit</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.26</td>
        <td>status + offset</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.27</td>
        <td>limit + offset</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.28</td>
        <td>status + limit + offset</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">1.29</td>
        <td>HTTP вместо HTTPS</td>
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
      <td>Accept-Language: EN</td>
      <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">2.2</td>
        <td>Без заголовка Accept-Language</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">2.3</td>
        <td>Несуществующий company_id</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">2.4</td>
        <td>Accept-Language: RU</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">2.5</td>
        <td>Accept-Language: PL</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">2.6</td>
        <td>company_id = 0</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">2.7</td>
        <td>company_id = отрицательное число</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">2.8</td>
        <td>company_id = строка</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">2.9</td>
        <td>company_id = дробное число</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">2.10</td>
        <td>Accept-Language = неподдерживаемое значение</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">2.11</td>
        <td>Accept-Language = пустое значение</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">2.12</td>
        <td>Accept-Language = несколько значений</td>
        <td align="center">Needs clarification</td>
    </tr>
    <tr>
        <td align="center">2.13</td>
        <td>Accept-Language в нижнем регистре</td>
        <td align="center">Needs clarification</td>
    </tr>
    <tr>
        <td align="center">2.14</td>
        <td>Идемпотентность повторного GET</td>
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
      <td>Без query-параметров</td>
      <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">3.2</td>
        <td>limit = корректное значение</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">3.3</td>
        <td>limit = минимально допустимое значение</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">3.4</td>
        <td>limit = 0</td>
        <td align="center">Fail</td>
    </tr>
    <tr>
        <td align="center">3.5</td>
        <td>limit = отрицательное число</td>
        <td align="center">Fail</td>
    </tr>
    <tr>
        <td align="center">3.6</td>
        <td>offset = корректное значение</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">3.7</td>
        <td>offset ≥ total</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">3.8</td>
        <td>offset = отрицательное число</td>
        <td align="center">Needs clarification</td>
    </tr>
    <tr>
        <td align="center">3.9</td>
        <td>limit = строка</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">3.10</td>
        <td>limit = пустое значение</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">3.11</td>
        <td>limit = дробное число</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">3.12</td>
        <td>offset = строка</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">3.13</td>
        <td>offset = пустое значение</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">3.14</td>
        <td>offset = дробное число</td>
        <td align="center">Pass</td>
    </tr>
      <tr>
        <td align="center">3.15</td>
        <td>limit + offset</td>
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
      <td>Существующий user_id</td>
      <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">4.2</td>
        <td>Несуществующий user_id</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">4.3</td>
        <td>user_id = 0</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">4.4</td>
        <td>user_id = отрицательное число</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">4.5</td>
        <td>user_id = строка</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">4.6</td>
        <td>user_id = дробное число</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">4.7</td>
        <td>Идемпотентность повторного GET</td>
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
      <td>Валидные значения всех полей в теле запроса</td>
      <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">5.2</td>
        <td>first_name = null</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">5.3</td>
        <td>last_name = null</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">5.4</td>
        <td>company_id = null</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">5.5</td>
        <td>Без обязательного поля last_name</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">5.6</td>
        <td>Компания со статусом CLOSED</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">5.7</td>
        <td>Компания со статусом BANKRUPT</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">5.8</td>
        <td>Несуществующий company_id</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">5.9</td>
        <td>Без тела запроса</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">5.10</td>
        <td>Два пользователя с одинаковыми данными</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">5.11</td>
        <td>Без необязательных полей (first_name, company_id)</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">5.12</td>
        <td>company_id = 0</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">5.13</td>
        <td>company_id = отрицательное число</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">5.14</td>
        <td>company_id = строка</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">5.15</td>
        <td>company_id = дробное число</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">5.16</td>
        <td>first_name = число</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">5.17</td>
        <td>last_name = число</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">5.18</td>
        <td>Невалидный JSON в теле запроса</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">5.19</td>
        <td>Content-Type: application/xml</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">5.20</td>
        <td>Без заголовка Content-Type</td>
        <td align="center">Needs clarification</td>
    </tr>
    <tr>
        <td align="center">5.21</td>
        <td>Дополнительное поле в теле запроса</td>
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
      <td>Валидные значения всех полей в теле запроса</td>
      <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.2</td>
        <td>first_name = null</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.3</td>
        <td>company_id = null</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.4</td>
        <td>last_name = null</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.5</td>
        <td>Компания со статусом CLOSED</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.6</td>
        <td>Компания со статусом BANKRUPT</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.7</td>
        <td>Несуществующий user_id</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.8</td>
        <td>Несуществующий company_id</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.9</td>
        <td>Без обязательного поля last_name</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.10</td>
        <td>Без тела запроса</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.11</td>
        <td>Идемпотентность повторного PUT</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.12</td>
        <td>user_id = строка</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.13</td>
        <td>Без необязательных полей (first_name, company_id)</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.14</td>
        <td>first_name = число</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.15</td>
        <td>last_name = число</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.16</td>
        <td>user_id = 0</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.17</td>
        <td>user_id = отрицательное число</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.18</td>
        <td>user_id = дробное число</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.19</td>
        <td>company_id = 0</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.20</td>
        <td>company_id = отрицательное число</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.21</td>
        <td>company_id = строка</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.22</td>
        <td>company_id = дробное число</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.23</td>
        <td>Без заголовка Content-Type</td>
        <td align="center">Needs clarification</td>
    </tr>
    <tr>
        <td align="center">6.24</td>
        <td>Content-Type: application/xml</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.25</td>
        <td>Невалидный JSON в теле запроса</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">6.26</td>
        <td>Дополнительное поле в теле запроса</td>
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
      <td>Удаление существующего пользователя</td>
      <td align="center">Fail</td>
    </tr>
    <tr>
        <td align="center">7.2</td>
        <td>Проверка повторного удаления ранее удалённого пользователя</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">7.3</td>
        <td>Несуществующий user_id</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">7.4</td>
        <td>user_id = строка</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">7.5</td>
        <td>user_id = 0</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">7.6</td>
        <td>user_id = отрицательное число</td>
        <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">7.7</td>
        <td>user_id = дробное число</td>
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
      <td>Полный цикл: create → get → update (другая компания) → get → delete → 404</td>
      <td align="center">Pass</td>
    </tr>
    <tr>
        <td align="center">8.2</td>
        <td>Пользователь в списке: появляется после create, исчезает после delete</td>
        <td align="center">Pass</td>
    </tr>
</table>

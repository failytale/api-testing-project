# REST API Testing Project

## :link: О проекте

Этот репозиторий содержит pet-project по ручному и автоматизированному тестированию REST API.

Цель проекта — продемонстрировать полный цикл тестирования REST API: от анализа спецификации до автоматизации проверок в Postman.

Проект подготовлен как демонстрация практических навыков Junior QA Engineer.

> _**Примечание**. Репозиторий регулярно обновляется по мере развития pet-проекта. На текущий момент полностью реализованы тестирование и автоматизация CRUD-операций для компаний и пользователей: подготовлена тестовая документация (чек-листы, тест-кейсы, баг-репорты), разработана и автоматизирована коллекция Postman, оформлены E2E-сценарии. В ближайшее время проект будет дополнен тестированием и автоматизацией модуля аутентификации (`/authorize`, `/me`), а также финальными улучшениями README_.

## :link: Тестируемый API

В рамках проекта тестируется REST API для работы с компаниями и пользователями.
- **Base URL**: `https://restapi.tech`
- **API version**: 0.1.0
- **Specification**: OpenAPI 3.1

### :white_small_square: Main endpoints

<table>
    <tr>
        <th>Endpoint</th>
        <th>Описание</th>
    </tr>
    <tr>
        <td><code>GET /api/companies</code></td>
        <td>Получение списка компаний с поддержкой фильтрации по статусу (<code>status</code>) и пагинации (<code>limit</code>, <code>offset</code>)</td>
    </tr>
    <tr>
        <td><code>GET&nbsp;/api/companies/{company_id}</code></td>
        <td>Получение информации о компании по идентификатору с поддержкой локализации ответа через заголовок <code>Accept-Language</code></td>
    </tr>
    <tr>
        <td><code>GET /api/users</code></td>
        <td>Получение списка пользователей с поддержкой пагинации (<code>limit</code>, <code>offset</code>)</td>
    </tr>
    <tr>
        <td><code>GET /api/users/{user_id}</code></td>
        <td>Получение информации о пользователе по идентификатору</td>
    </tr>
    <tr>
        <td><code>POST /api/users</code></td>
        <td>Создание нового пользователя</td>
    </tr>
    <tr>
        <td><code>PUT /api/users/{user_id}</code></td>
        <td>Обновление данных существующего пользователя</td>
    </tr>
    <tr>
        <td><code>DELETE /api/users/{user_id}</code></td>
        <td>Удаление пользователя по идентификатору</td>
    </tr>
</table>

### :white_small_square: Authentication

<table>
    <tr>
        <th>Endpoint</th>
        <th>Описание</th>
    </tr>
    <tr>
        <td><code>POST /authorize</code></td>
        <td>Аутентификация пользователя и получение токена доступа</td>
    </tr>
    <tr>
        <td><code>GET /me</code></td>
        <td>Получение информации о текущем авторизованном пользователе</td>
    </tr>
</table>

### :white_small_square: Issue endpoints

В тестируемом API есть отдельный блок endpoint’ов `/api/issues/*`, содержащий изолированные сценарии с дефектами. Для этого блока были переиспользованы релевантные проверки из основного набора тестов. Найденные расхождения между ожидаемым и фактическим поведением оформлены в виде баг-репортов.

<table>
    <tr>
        <th>Endpoint</th>
        <th>Описание</th>
    </tr>
    <tr>
        <td><code>GET /api/issues/companies</code></td>
        <td>Получение списка компаний с преднамеренно внедрёнными дефектами</td>
    </tr>
    <tr>
        <td><code>GET&nbsp;/api/issues/companies/{company_id}</code></td>
        <td>Получение информации о компании с преднамеренно внедрёнными дефектами</td>
    </tr>
    <tr>
        <td><code>GET /api/issues/users/{user_id}</code></td>
        <td>Получение информации о пользователе с преднамеренно внедрёнными дефектами</td>
    </tr>
    <tr>
        <td><code>POST /api/issues/users</code></td>
        <td>Создание пользователя с преднамеренно внедрёнными дефектами</td>
    </tr>
</table>

## :link: Подход к тестированию

Тестирование проекта выполнялось поэтапно в соответствии с основными этапами жизненного цикла тестирования. Работа начиналась с анализа OpenAPI-спецификации, после чего проектировались тесты с использованием техник тест-дизайна (классы эквивалентности, анализ граничных значений и комбинаторное тестирование параметров запросов), подготавливалась тестовая документация (чек-листы и тест-кейсы), выполнялось ручное тестирование, обнаруженные дефекты оформлялись в баг-репорты и автоматизировались основные сценарии в Postman.

### :white_small_square: Область тестирования

В рамках проекта проверяется корректность работы CRUD-операций для компаний и пользователей, а также сценариев аутентификации. Особое внимание уделено позитивным, негативным и End-to-End сценариям, обработке ошибок, проверке бизнес-правил, обязательных и необязательных параметров, типов данных, query- и path-параметров, структуры JSON-ответов, статус-кодов, заголовков ответа, фильтрации, пагинации и свойств HTTP-методов.

### :white_small_square: Ограничения проекта

Проект ориентирован на функциональное тестирование. В его рамках не выполняются нагрузочное тестирование, тестирование производительности под высокой нагрузкой, полноценное security-тестирование и непосредственная проверка данных в базе данных, поскольку доступ к ней отсутствует. При этом отдельные проверки устойчивости API к некорректным входным данным (например, передача SQL-like строк в параметрах запроса) выполняются точечно, однако не рассматриваются как полноценный аудит безопасности.

### :white_small_square: Подход к тестовым данным

Для `GET`-запросов используются заранее существующие неизменяемые (read-only) данные. Для сценариев, изменяющих состояние системы (`POST`, `PUT`, `DELETE`), тестовые данные создаются динамически непосредственно перед выполнением проверки и удаляются после её завершения. Такой подход обеспечивает независимость тестов, возможность их повторного выполнения и исключает влияние предыдущих сценариев на последующие.

### :white_small_square: Работа с неоднозначными требованиями

В качестве источника ожидаемого поведения используется OpenAPI-спецификация. Если поведение API отсутствует в документации или описано неоднозначно, соответствующий сценарий помечается как `Needs clarification`. До получения уточнений такие проверки не классифицируются как `Pass` или `Fail` и не рассматриваются как подтверждённые дефекты.

## :link: Найденные дефекты 

<table>
    <tr>
        <th>ID</th>
        <th>Название</th>
        <th>Severity</th>
        <th>Priority</th>
    </tr>
    <tr>
        <td align="center" nowrap><a href="docs/bug-reports/bug-reports.md#bug-001-get-apicompanies-не-возвращает-ошибку-валидации-при-передаче-limit0">BUG-001</a></td>
        <td><code>GET /api/companies</code> не возвращает ошибку валидации при передаче <code>limit=0</code></td>
        <td align="center">Minor</td>
        <td align="center">Medium</td>
    </tr>
    <tr>
        <td align="center"><a href="docs/bug-reports/bug-reports.md#bug-002-get-apicompanies-возвращает-все-компании-при-передаче-limit-1-вместо-ошибки-валидации">BUG-002</a></td>
        <td><code>GET /api/companies</code> возвращает все компании при передаче <code>limit=-1</code> вместо ошибки валидации</td>
        <td align="center">Major</td>
        <td align="center">Medium</td>
    </tr>
    <tr>
        <td align="center"><a href="docs/bug-reports/bug-reports.md#bug-003-get-apiusers-не-возвращает-ошибку-валидации-при-передаче-limit0">BUG-003</a></td>
        <td><code>GET /api/users</code> не возвращает ошибку валидации при передаче <code>limit=0</code></td>
        <td align="center">Minor</td>
        <td align="center">Medium</td>
    </tr>
    <tr>
        <td align="center"><a href="docs/bug-reports/bug-reports.md#bug-004-get-apiusers-возвращает-пользователей-при-передаче-limit-1-вместо-ошибки-валидации">BUG-004</a></td>
        <td><code>GET /api/users</code> возвращает пользователей при передаче <code>limit=-1</code> вместо ошибки валидации</td>
        <td align="center">Major</td>
        <td align="center">Medium</td>
    </tr>
    <tr>
        <td align="center"><a href="docs/bug-reports/bug-reports.md#bug-005-delete-apiusersuser_id-возвращает-null-вместо-json-объекта">BUG-005</a></td>
        <td><code>DELETE /api/users/{user_id}</code> возвращает <code>null</code> вместо JSON-объекта</td>
        <td align="center">Minor</td>
        <td align="center">Medium</td>
    </tr>
    <tr>
        <td align="center"><a href="docs/bug-reports/bug-reports.md#bug-006-get-apiissuescompanies-игнорирует-значение-query-параметра-status">BUG-006</a></td>
        <td><code>GET /api/issues/companies</code> игнорирует значение query-параметра <code>status</code></td>
        <td align="center">Major</td>
        <td align="center">Medium</td>
    </tr>
    <tr>
        <td align="center"><a href="docs/bug-reports/bug-reports.md#bug-007-время-ответа-get-apiissuescompaniescompany_id-превышает-допустимое-значение">BUG-007</a></td>
        <td>Время ответа <code>GET /api/issues/companies/{company_id}</code> превышает допустимое значение</td>
        <td align="center">Major</td>
        <td align="center">Medium</td>
    </tr>
    <tr>
        <td align="center"><a href="docs/bug-reports/bug-reports.md#bug-008-get-apiissuesusersuser_id-возвращает-202-accepted-вместо-200-ok">BUG-008</a></td>
        <td><code>GET /api/issues/users/{user_id}</code> возвращает <code>202 Accepted</code> вместо <code>200 OK</code></td>
        <td align="center">Minor</td>
        <td align="center">Medium</td>
    </tr>
    <tr>
        <td align="center"><a href="docs/bug-reports/bug-reports.md#bug-009-ответ-get-apiissuesusersuser_id-не-содержит-обязательное-поле-user_id">BUG-009</a></td>
        <td>Ответ <code>GET /api/issues/users/{user_id}</code> не содержит обязательное поле <code>user_id</code></td>
        <td align="center">Major</td>
        <td align="center">Medium</td>
    </tr>
    <tr>
        <td align="center"><a href="docs/bug-reports/bug-reports.md#bug-010-get-apiissuesusersuser_id-возвращает-500-internal-server-error-для-пользователя-с-null-в-полях">BUG-010</a></td>
        <td><code>GET /api/issues/users/{user_id}</code> возвращает <code>500 Internal Server Error</code> для пользователя с <code>null</code> в полях</td>
        <td align="center">Major</td>
        <td align="center">High</td>
    </tr>
    <tr>
        <td align="center"><a href="docs/bug-reports/bug-reports.md#bug-011-post-apiissuesusers-возвращает-значения-полей-отличающиеся-от-переданных-в-запросе">BUG-011</a></td>
        <td><code>POST /api/issues/users</code> возвращает значения полей, отличающиеся от переданных в запросе</td>
        <td align="center">Major</td>
        <td align="center">High</td>
    </tr>
</table>

## :link: Документация проекта

- [Чек-лист](docs/checklist/checklist.md) — высокоуровневый список проверок, сгруппированный по endpoint’ам.
- [Тест-кейсы](docs/test-cases/) — подробное описание проверок для позитивных, негативных и E2E-сценариев.
- [Баг-репорты](docs/bug-reports/bug-reports.md) — описание обнаруженных дефектов.
- [Схемы ответов](docs/schemas/response-schemas.md) — описание JSON-схем, используемых для проверки структуры тела ответа.

## :link: Postman-коллекция

[Коллекция](postman/collection/) содержит автоматизированные проверки, реализованные с использованием встроенных возможностей Postman. В ней используются:

- **Переменные коллекции** — для хранения JSON-cхем, тестовых данных и значений, полученных во время выполнения сценариев.
- **Инициализация JSON-схем** (`00_Setup`) — для загрузки JSON-схем в переменные коллекции перед запуском тестов.
- **Pre-request scripts** — для подготовки тестовых данных, создания зависимых сущностей и передачи данных между запросами.
- **Post-response scripts** — для автоматизированной проверки HTTP статус-кодов, заголовков ответа, времени ответа, структуры ответа (JSON Schema Validation), бизнес-логики и содержимого тела ответа.
- **Очистка тестовых данных** — для удаления тестовых данных после выполнения сценариев и обеспечения независимости тестов.

### :white_small_square: Запуск коллекции

1. Импортировать коллекцию в Postman.
2. Выполнить запрос `00_Setup` для инициализации JSON Schemas в переменных коллекции.
3. Запустить коллекцию через `Run collection`.
4. После завершения выполнения ознакомиться с результатами во вкладке `Runs`.

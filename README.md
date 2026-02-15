<h1>
  SQL <img src="./assets/sql.svg" width="40" height="40" />
</h1>

<h2>Найпопулярніші запитання та відповіді на співбесіді з SQL</h2>

<details>
<summary>1. Що таке SQL?</summary>

#### SQL

SQL (Structured Query Language) - це стандартизована мова для роботи з реляційними базами даних.
SQL дозволяє читати дані, змінювати їх, керувати структурою таблиць, транзакціями та правами доступу.

```sql
SELECT id, full_name
FROM users
WHERE is_active = TRUE;
```

**Коротко:**

- SQL - стандартна мова для реляційних БД.
- Основні задачі: читання, зміна даних, керування схемою і доступом.
- SQL працює у більшості сучасних СУБД.

</details>

<details>
<summary>2. Для чого використовується SQL?</summary>

#### SQL

SQL використовується для повного циклу роботи з даними:

- отримання і фільтрація записів;
- вставка, оновлення і видалення даних;
- об'єднання даних з кількох таблиць;
- контроль цілісності через ключі та обмеження;
- керування транзакціями і правами доступу.

```sql
SELECT p.name, c.name AS category_name
FROM products p
JOIN categories c ON c.id = p.category_id;
```

**Коротко:**

- SQL застосовується для всіх базових операцій із даними.
- Через SQL будують запити для backend, аналітики та звітів.
- SQL також контролює цілісність і безпеку даних.

</details>

<details>
<summary>3. У чому різниця між SQL і MySQL?</summary>

#### SQL

`SQL` - це мова запитів (стандарт).
`MySQL` - це конкретна СУБД, яка реалізує SQL.

Це означає:

- SQL визначає синтаксис і принципи роботи із реляційними даними;
- MySQL виконує SQL-запити і зберігає дані;
- окрім MySQL існують інші SQL-СУБД: PostgreSQL, SQL Server, Oracle, SQLite.

```sql
SELECT email
FROM users
WHERE id = 10;
```

**Коротко:**

- SQL = мова.
- MySQL = продукт (СУБД).
- Одна мова SQL використовується у різних СУБД з діалектними відмінностями.

</details>

<details>
<summary>4. Які основні типи SQL-команд існують?</summary>

#### SQL

Основні категорії SQL-команд:

1. `DDL` - керування структурою БД.
- `CREATE`, `ALTER`, `DROP`, `TRUNCATE`.

2. `DML` - зміна даних.
- `INSERT`, `UPDATE`, `DELETE`, `MERGE`.

3. `DQL` - запити на читання.
- `SELECT`.

4. `DCL` - керування правами.
- `GRANT`, `REVOKE`.

5. `TCL` - керування транзакціями.
- `BEGIN`, `COMMIT`, `ROLLBACK`, `SAVEPOINT`.

```sql
BEGIN;
UPDATE accounts SET balance = balance - 100 WHERE id = 1;
UPDATE accounts SET balance = balance + 100 WHERE id = 2;
COMMIT;
```

**Коротко:**

- `DDL` керує схемою.
- `DML`/`DQL` керують даними.
- `DCL` і `TCL` керують доступом і транзакціями.

</details>

<details>
<summary>5. Що таке база даних?</summary>

#### SQL

База даних - це організоване сховище взаємопов'язаних даних, яким керує СУБД.
У реляційній моделі дані зберігаються в таблицях, пов'язаних ключами.

Ключові властивості реляційної БД:

- структурованість (схема);
- цілісність (обмеження і ключі);
- надійність змін через транзакції;
- ефективний доступ через SQL.

**Коротко:**

- БД зберігає структуровані дані.
- Реляційна БД працює через таблиці та зв'язки.
- СУБД забезпечує цілісність, транзакційність і доступ до даних.

</details>

<details>
<summary>6. Що таке таблиця?</summary>

#### SQL

Таблиця - це об'єкт БД, у якому дані зберігаються у вигляді стовпців і рядків.
Стовпці описують структуру даних (типи, обмеження), рядки містять конкретні записи.

```sql
CREATE TABLE customers (
  customer_id BIGINT PRIMARY KEY,
  full_name VARCHAR(200) NOT NULL,
  email VARCHAR(255) UNIQUE,
  created_at TIMESTAMP NOT NULL
);
```

**Коротко:**

- Таблиця зберігає дані однієї сутності.
- Стовпці = структура, рядки = записи.
- Таблиця створюється через DDL-команди.

</details>

<details>
<summary>7. Що таке рядок і стовпець у таблиці?</summary>

#### SQL

Стовпець (`column`) - це поле таблиці з визначеним типом даних і правилами.
Рядок (`row`) - це один запис із конкретними значеннями у стовпцях.

```sql
SELECT customer_id, full_name, email
FROM customers
WHERE customer_id = 101;
```

У прикладі:

- `customer_id`, `full_name`, `email` - стовпці;
- результат для `customer_id = 101` - рядок.

**Коротко:**

- Стовпець = атрибут.
- Рядок = один запис.
- Таблиця = багато рядків однакової структури.

</details>

<details>
<summary>8. Що таке первинний ключ (Primary Key)?</summary>

#### SQL

`PRIMARY KEY` - це стовпець або набір стовпців, що унікально ідентифікує кожен рядок таблиці.

Властивості:

- тільки унікальні значення;
- `NULL` не допускається;
- один primary key на таблицю (може бути складеним).

```sql
CREATE TABLE orders (
  order_id BIGINT PRIMARY KEY,
  customer_id BIGINT NOT NULL,
  total_amount NUMERIC(12,2) NOT NULL
);
```

**Коротко:**

- `PRIMARY KEY` однозначно визначає рядок.
- Не допускає `NULL` і дублікати.
- Використовується як база для зв'язків між таблицями.

</details>

<details>
<summary>9. Що таке зовнішній ключ (Foreign Key)?</summary>

#### SQL

`FOREIGN KEY` - це обмеження, яке задає зв'язок між дочірньою та батьківською таблицями.
Воно гарантує, що значення в дочірній таблиці посилається на існуючий запис у батьківській.

```sql
CREATE TABLE orders (
  order_id BIGINT PRIMARY KEY,
  customer_id BIGINT NOT NULL,
  CONSTRAINT fk_orders_customer
    FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
);
```

Типові правила поведінки:

- `ON DELETE RESTRICT` / `NO ACTION`;
- `ON DELETE CASCADE`;
- `ON DELETE SET NULL`.

**Коротко:**

- `FOREIGN KEY` створює зв'язок між таблицями.
- Захищає від невалідних посилань.
- Поведінку при видаленні/оновленні задають правила `ON DELETE`/`ON UPDATE`.

</details>

<details>
<summary>10. Що таке обмеження (constraints) у SQL?</summary>

#### SQL

`Constraints` - це правила на рівні БД, які контролюють допустимі значення й зв'язки між даними.

Основні обмеження:

- `NOT NULL`;
- `UNIQUE`;
- `PRIMARY KEY`;
- `FOREIGN KEY`;
- `CHECK`;
- `DEFAULT`.

```sql
CREATE TABLE users (
  user_id BIGINT PRIMARY KEY,
  email VARCHAR(255) NOT NULL UNIQUE,
  age INT CHECK (age >= 16),
  status VARCHAR(20) DEFAULT 'active'
);
```

**Коротко:**

- Обмеження забезпечують цілісність і якість даних.
- Найкритичніші: `PRIMARY KEY`, `FOREIGN KEY`, `NOT NULL`, `UNIQUE`, `CHECK`.
- Валідація на рівні БД зменшує ризик некоректних даних.

</details>
<details>
<summary>11. Що таке NOT NULL?</summary>

#### SQL

`NOT NULL` - це обмеження, яке забороняє зберігати `NULL` у стовпці.
Тобто значення для такого поля обов'язкове при вставці та оновленні.

```sql
CREATE TABLE employees (
  id BIGINT PRIMARY KEY,
  full_name VARCHAR(200) NOT NULL
);
```

**Коротко:**

- `NOT NULL` забороняє порожнє значення `NULL`.
- Поле з `NOT NULL` обов'язкове для заповнення.
- Використовується для критично важливих атрибутів.

</details>

<details>
<summary>12. Що таке UNIQUE?</summary>

#### SQL

`UNIQUE` - це обмеження, яке гарантує унікальність значень у стовпці або комбінації стовпців.
Дублікати заборонені.

```sql
CREATE TABLE users (
  id BIGINT PRIMARY KEY,
  email VARCHAR(255) NOT NULL UNIQUE
);
```

Приклад складеного `UNIQUE`:

```sql
CREATE TABLE user_roles (
  user_id BIGINT NOT NULL,
  role_id BIGINT NOT NULL,
  CONSTRAINT uq_user_role UNIQUE (user_id, role_id)
);
```

**Коротко:**

- `UNIQUE` не дозволяє дублювати значення.
- Працює для одного або кількох стовпців.
- Часто застосовується для `email`, `username`, бізнес-ідентифікаторів.

</details>

<details>
<summary>13. Що таке DEFAULT?</summary>

#### SQL

`DEFAULT` задає значення за замовчуванням, яке БД підставляє, якщо поле не передано в `INSERT`.

```sql
CREATE TABLE tasks (
  id BIGINT PRIMARY KEY,
  status VARCHAR(20) NOT NULL DEFAULT 'new',
  created_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP
);
```

**Коротко:**

- `DEFAULT` підставляє значення автоматично.
- Зменшує кількість `NULL` і спрощує вставку даних.
- Типові значення: статус, дата створення, прапорець активності.

</details>

<details>
<summary>14. Що таке CHECK?</summary>

#### SQL

`CHECK` - це обмеження, яке перевіряє умову для значення стовпця або рядка.
Якщо умова хибна, запис не вставляється/не оновлюється.

```sql
CREATE TABLE products (
  id BIGINT PRIMARY KEY,
  price NUMERIC(10,2) NOT NULL CHECK (price >= 0),
  discount_percent INT CHECK (discount_percent BETWEEN 0 AND 100)
);
```

**Коротко:**

- `CHECK` валідовує дані на рівні БД.
- Захищає від невалідних значень.
- Працює як для одного поля, так і для комбінації полів.

</details>

<details>
<summary>15. Що таке AUTO INCREMENT?</summary>

#### SQL

`AUTO INCREMENT`/автогенерація ключа - це механізм автоматичного створення нового числового `id` для кожного запису.

У сучасному SQL частіше використовують:

- `GENERATED ... AS IDENTITY` (стандартний підхід);
- або діалектні варіанти (`AUTO_INCREMENT` у MySQL, `SERIAL`/`IDENTITY` у PostgreSQL, `IDENTITY` у SQL Server).

```sql
CREATE TABLE orders (
  id BIGINT GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
  total_amount NUMERIC(12,2) NOT NULL
);
```

**Коротко:**

- Автогенерація створює унікальний числовий ключ автоматично.
- Для нових схем краще `IDENTITY`-підхід.
- Діалектний синтаксис залежить від СУБД.

</details>

<details>
<summary>16. Як створити таблицю в SQL?</summary>

#### SQL

Таблиця створюється командою `CREATE TABLE`, де задаються:

- назви стовпців;
- типи даних;
- обмеження (`PRIMARY KEY`, `NOT NULL`, `UNIQUE`, `CHECK`, `DEFAULT`, `FOREIGN KEY`).

```sql
CREATE TABLE customers (
  customer_id BIGINT GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
  full_name VARCHAR(200) NOT NULL,
  email VARCHAR(255) NOT NULL UNIQUE,
  is_active BOOLEAN NOT NULL DEFAULT TRUE,
  created_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP
);
```

**Коротко:**

- `CREATE TABLE` створює нову таблицю.
- Обов'язково визначають типи й ключові обмеження.
- Коректна схема одразу зменшує кількість помилок у даних.

</details>

<details>
<summary>17. Як змінити структуру таблиці?</summary>

#### SQL

Структуру таблиці змінюють командою `ALTER TABLE`.
Нею можна додавати/видаляти стовпці, змінювати типи, додавати обмеження та індекси.

```sql
ALTER TABLE customers
ADD COLUMN phone VARCHAR(30);
```

```sql
ALTER TABLE customers
ALTER COLUMN full_name TYPE VARCHAR(255);
```

**Коротко:**

- Для змін схеми використовують `ALTER TABLE`.
- Зміни варто робити через керовані міграції.
- Перед зміною типів і видаленням полів потрібно перевіряти залежності.

</details>

<details>
<summary>18. Як видалити таблицю?</summary>

#### SQL

Таблицю видаляють командою `DROP TABLE`.
Операція видаляє і структуру, і всі дані таблиці.

```sql
DROP TABLE archived_orders;
```

Безпечніший варіант:

```sql
DROP TABLE IF EXISTS archived_orders;
```

**Коротко:**

- `DROP TABLE` повністю видаляє таблицю.
- `IF EXISTS` допомагає уникнути помилки, якщо таблиці немає.
- Перед виконанням потрібно врахувати зовнішні ключі та залежності.

</details>

<details>
<summary>19. Як додати новий стовпець у таблицю?</summary>

#### SQL

Новий стовпець додають через `ALTER TABLE ... ADD COLUMN`.

```sql
ALTER TABLE users
ADD COLUMN last_login_at TIMESTAMP;
```

Можна одразу додати обмеження:

```sql
ALTER TABLE users
ADD COLUMN status VARCHAR(20) NOT NULL DEFAULT 'active';
```

**Коротко:**

- Додавання поля: `ALTER TABLE ... ADD COLUMN`.
- Для обов'язкових полів краще задавати `DEFAULT`.
- Після зміни схеми варто перевірити запити й індекси.

</details>

<details>
<summary>20. Як видалити стовпець із таблиці?</summary>

#### SQL

Стовпець видаляють командою `ALTER TABLE ... DROP COLUMN`.

```sql
ALTER TABLE users
DROP COLUMN middle_name;
```

Перед видаленням треба перевірити, чи не використовується стовпець у:

- індексах;
- обмеженнях;
- view/materialized view;
- SQL-запитах застосунку.

**Коротко:**

- Видалення поля: `ALTER TABLE ... DROP COLUMN`.
- Це потенційно незворотна зміна даних.
- Спочатку перевіряють усі залежності.

</details>

<details>
<summary>21. Що таке оператор SELECT?</summary>

#### SQL

`SELECT` - це основний SQL-оператор для читання даних з однієї або кількох таблиць.
Він підтримує фільтрацію, сортування, агрегацію, об'єднання та підзапити.

```sql
SELECT id, full_name
FROM users
WHERE is_active = TRUE
ORDER BY full_name;
```

**Коротко:**

- `SELECT` використовується для вибірки даних.
- Працює з `WHERE`, `JOIN`, `GROUP BY`, `ORDER BY`.
- Це базова команда для звітів, API і аналітики.

</details>

<details>
<summary>22. Як вибрати всі записи з таблиці?</summary>

#### SQL

Щоб вибрати всі рядки таблиці, використовують `SELECT ... FROM`.

```sql
SELECT *
FROM users;
```

`*` означає всі стовпці.
У production-запитах краще явно вказувати потрібні стовпці для продуктивності та стабільності контракту даних.

**Коротко:**

- Усі записи: `SELECT * FROM table_name`.
- `*` повертає всі стовпці.
- Для робочих запитів краще перелічувати колонки явно.

</details>

<details>
<summary>23. Як вибрати лише певні стовпці?</summary>

#### SQL

Потрібні стовпці вказують списком після `SELECT`.

```sql
SELECT id, full_name, email
FROM users;
```

Можна задавати псевдоніми:

```sql
SELECT full_name AS name, created_at AS registered_at
FROM users;
```

**Коротко:**

- Для вибірки частини полів перераховують їх у `SELECT`.
- Це зменшує обсяг даних і навантаження.
- Псевдоніми (`AS`) роблять результат читабельнішим.

</details>

<details>
<summary>24. Як використовувати WHERE?</summary>

#### SQL

`WHERE` фільтрує рядки за умовою до сортування та групування.
Підтримує логічні оператори `AND`, `OR`, `NOT`, а також `IN`, `BETWEEN`, `LIKE`, `IS NULL`.

```sql
SELECT id, full_name, salary
FROM employees
WHERE is_active = TRUE
  AND salary >= 2000;
```

```sql
SELECT id, email
FROM users
WHERE email LIKE '%@company.com';
```

**Коротко:**

- `WHERE` залишає тільки рядки, що відповідають умові.
- Умови можна комбінувати логічними операторами.
- Для `NULL` потрібно `IS NULL` / `IS NOT NULL`, а не `= NULL`.

</details>

<details>
<summary>25. Які оператори порівняння використовуються в SQL?</summary>

#### SQL

Базові оператори порівняння:

- `=` дорівнює;
- `<>` або `!=` не дорівнює (залежить від діалекту, `<>` більш стандартний);
- `>` більше;
- `<` менше;
- `>=` більше або дорівнює;
- `<=` менше або дорівнює.

Додаткові оператори/предикати для умов:

- `BETWEEN ... AND ...`;
- `IN (...)`;
- `LIKE` / `ILIKE` (діалектно);
- `IS NULL` / `IS NOT NULL`.

```sql
SELECT *
FROM products
WHERE price >= 100
  AND price <= 500
  AND category_id IN (1, 2, 3);
```

**Коротко:**

- Основні оператори: `=`, `<>`, `>`, `<`, `>=`, `<=`.
- Для наборів і діапазонів зручно `IN` і `BETWEEN`.
- Для `NULL` використовують тільки `IS NULL` / `IS NOT NULL`.

</details>


<details>
<summary>26. Як працює оператор BETWEEN?</summary>

#### SQL

`BETWEEN` перевіряє, чи значення входить у діапазон включно з обома межами.
Еквівалент: `value >= min AND value <= max`.

```sql
SELECT order_id, total_amount
FROM orders
WHERE total_amount BETWEEN 100 AND 500;
```

Для дат:

```sql
SELECT *
FROM orders
WHERE created_at BETWEEN DATE '2026-01-01' AND DATE '2026-01-31';
```

**Коротко:**

- `BETWEEN` задає діапазон із включеними межами.
- Працює для чисел, дат, часу.
- Аналог двох умов через `>=` і `<=`.

</details>

<details>
<summary>27. Як працює оператор IN?</summary>

#### SQL

`IN` перевіряє, чи значення дорівнює одному зі значень у списку або підзапиті.
Це компактна заміна кількох `OR`.

```sql
SELECT *
FROM products
WHERE category_id IN (1, 2, 3);
```

```sql
SELECT *
FROM users
WHERE id IN (
  SELECT user_id
  FROM active_sessions
);
```

**Коротко:**

- `IN` перевіряє належність до набору значень.
- Зручніше за довгий ланцюг `OR`.
- Працює зі списком і підзапитом.

</details>

<details>
<summary>28. Як працює оператор LIKE?</summary>

#### SQL

`LIKE` використовується для шаблонного пошуку в рядках.
Основні wildcard-символи:

- `%` - будь-яка кількість символів;
- `_` - рівно один символ.

```sql
SELECT *
FROM users
WHERE email LIKE '%@company.com';
```

```sql
SELECT *
FROM products
WHERE name LIKE 'Pro_%';
```

**Коротко:**

- `LIKE` шукає текст за шаблоном.
- `%` = 0+ символів, `_` = 1 символ.
- Найчастіше використовується для часткового пошуку.

</details>

<details>
<summary>29. У чому різниця між LIKE і ILIKE?</summary>

#### SQL

`LIKE` зазвичай чутливий до регістру, `ILIKE` - нечутливий до регістру (діалектно, наприклад у PostgreSQL).

```sql
-- PostgreSQL
SELECT *
FROM users
WHERE full_name ILIKE '%ivan%';
```

Портативний варіант для СУБД без `ILIKE`:

```sql
SELECT *
FROM users
WHERE LOWER(full_name) LIKE LOWER('%ivan%');
```

**Коротко:**

- `LIKE` частіше case-sensitive.
- `ILIKE` case-insensitive (не у всіх СУБД).
- Для сумісності можна застосовувати `LOWER(...)`.

</details>

<details>
<summary>30. Що таке сортування даних (ORDER BY)?</summary>

#### SQL

`ORDER BY` сортує результат запиту за одним або кількома стовпцями.
Напрямок: `ASC` (за замовчуванням) або `DESC`.

```sql
SELECT id, full_name, created_at
FROM users
ORDER BY created_at DESC, full_name ASC;
```

**Коротко:**

- `ORDER BY` визначає порядок рядків у результаті.
- Підтримує мультисортування.
- `ASC` зростання, `DESC` спадання.

</details>

<details>
<summary>31. Як обмежити кількість результатів (LIMIT)?</summary>

#### SQL

`LIMIT` обмежує кількість рядків у результаті запиту.
Часто використовується для пагінації та попереднього перегляду.

```sql
SELECT *
FROM logs
ORDER BY created_at DESC
LIMIT 20;
```

**Коротко:**

- `LIMIT N` повертає не більше `N` рядків.
- Зазвичай комбінується з `ORDER BY`.
- Корисний для пагінації та тестових вибірок.

</details>

<details>
<summary>32. Що таке OFFSET?</summary>

#### SQL

`OFFSET` пропускає вказану кількість рядків перед поверненням результату.
Зазвичай йде разом із `LIMIT`.

```sql
SELECT *
FROM users
ORDER BY id
LIMIT 10 OFFSET 20;
```

Цей приклад повертає 10 рядків, починаючи з 21-го.

**Коротко:**

- `OFFSET` пропускає перші `N` рядків.
- Використовується для сторінкової навігації.
- Для стабільного результату потрібен `ORDER BY`.

</details>

<details>
<summary>33. Що таке DISTINCT?</summary>

#### SQL

`DISTINCT` прибирає дублікати в результаті `SELECT`.
Унікальність визначається за всіма стовпцями, що вказані в `SELECT`.

```sql
SELECT DISTINCT country
FROM customers;
```

```sql
SELECT DISTINCT city, country
FROM customers;
```

**Коротко:**

- `DISTINCT` повертає лише унікальні значення.
- Працює по комбінації вибраних колонок.
- Часто використовується для довідкових списків.

</details>

<details>
<summary>34. Як працює GROUP BY?</summary>

#### SQL

`GROUP BY` групує рядки з однаковими значеннями в групи.
Зазвичай застосовується разом з агрегатними функціями.

```sql
SELECT department_id, COUNT(*) AS employees_count
FROM employees
GROUP BY department_id;
```

Правило: усі неагреговані стовпці в `SELECT` мають бути в `GROUP BY`.

**Коротко:**

- `GROUP BY` об'єднує рядки у групи.
- Використовується разом із `COUNT`, `SUM`, `AVG`, `MIN`, `MAX`.
- Неагреговані поля треба включати в `GROUP BY`.

</details>

<details>
<summary>35. Що таке агрегатні функції?</summary>

#### SQL

Агрегатні функції обчислюють одне підсумкове значення по набору рядків.
Вони працюють для всієї вибірки або для кожної групи після `GROUP BY`.

```sql
SELECT COUNT(*) AS total_orders,
       SUM(total_amount) AS revenue
FROM orders;
```

**Коротко:**

- Агрегатні функції зводять багато рядків до одного значення.
- Працюють глобально або по групах.
- Основа звітності та аналітики в SQL.

</details>

<details>
<summary>36. Які основні агрегатні функції існують?</summary>

#### SQL

Найпоширеніші агрегатні функції:

- `COUNT()` - кількість рядків;
- `SUM()` - сума;
- `AVG()` - середнє;
- `MIN()` - мінімум;
- `MAX()` - максимум.

```sql
SELECT COUNT(*) AS total,
       SUM(amount) AS total_amount,
       AVG(amount) AS avg_amount,
       MIN(amount) AS min_amount,
       MAX(amount) AS max_amount
FROM payments;
```

**Коротко:**

- Базові агрегати: `COUNT`, `SUM`, `AVG`, `MIN`, `MAX`.
- Використовуються у звітах та метриках.
- Часто комбінуються з `GROUP BY`.

</details>

<details>
<summary>37. Що таке HAVING?</summary>

#### SQL

`HAVING` фільтрує вже згруповані дані після `GROUP BY`.
На відміну від `WHERE`, він працює з агрегатами.

```sql
SELECT department_id, COUNT(*) AS employees_count
FROM employees
GROUP BY department_id
HAVING COUNT(*) >= 5;
```

**Коротко:**

- `HAVING` фільтрує групи, а не окремі рядки.
- Використовується після `GROUP BY`.
- Дозволяє умови з агрегатними функціями.

</details>

<details>
<summary>38. У чому різниця між WHERE і HAVING?</summary>

#### SQL

Різниця в етапі обробки:

- `WHERE` - фільтрація рядків до групування;
- `HAVING` - фільтрація груп після `GROUP BY`.

```sql
SELECT department_id, AVG(salary) AS avg_salary
FROM employees
WHERE is_active = TRUE
GROUP BY department_id
HAVING AVG(salary) > 3000;
```

**Коротко:**

- `WHERE` працює з рядками до агрегації.
- `HAVING` працює з результатами агрегації.
- У складних запитах зазвичай використовують обидва.

</details>

<details>
<summary>39. Як порахувати кількість записів?</summary>

#### SQL

Для підрахунку рядків використовують `COUNT()`.

```sql
SELECT COUNT(*) AS total_users
FROM users;
```

Підрахунок ненульових значень у колонці:

```sql
SELECT COUNT(phone) AS users_with_phone
FROM users;
```

Підрахунок унікальних значень:

```sql
SELECT COUNT(DISTINCT country) AS unique_countries
FROM users;
```

**Коротко:**

- Кількість усіх рядків: `COUNT(*)`.
- Кількість ненульових значень: `COUNT(column)`.
- Кількість унікальних: `COUNT(DISTINCT column)`.

</details>

<details>
<summary>40. Як знайти максимальне або мінімальне значення?</summary>

#### SQL

Для цього використовують `MAX()` і `MIN()`.

```sql
SELECT MAX(price) AS max_price,
       MIN(price) AS min_price
FROM products;
```

У межах груп:

```sql
SELECT category_id,
       MAX(price) AS max_price,
       MIN(price) AS min_price
FROM products
GROUP BY category_id;
```

**Коротко:**

- `MAX()` повертає найбільше значення.
- `MIN()` повертає найменше значення.
- Часто застосовуються з `GROUP BY`.

</details>

<details>
<summary>41. Що таке JOIN?</summary>

#### SQL

`JOIN` - це механізм об'єднання рядків із кількох таблиць за умовою зв'язку.
Зазвичай зв'язок задається через ключі (`PRIMARY KEY` ↔ `FOREIGN KEY`).

```sql
SELECT o.order_id, c.full_name
FROM orders o
JOIN customers c ON c.customer_id = o.customer_id;
```

**Коротко:**

- `JOIN` об'єднує дані з різних таблиць.
- Зв'язок визначається умовою `ON`.
- Основа нормалізованої реляційної моделі.

</details>

<details>
<summary>42. У чому різниця між INNER JOIN і LEFT JOIN?</summary>

#### SQL

- `INNER JOIN` повертає тільки рядки, де збіг є в обох таблицях.
- `LEFT JOIN` повертає всі рядки лівої таблиці і збіги з правої; якщо збігу немає - поля правої таблиці будуть `NULL`.

```sql
SELECT c.customer_id, o.order_id
FROM customers c
INNER JOIN orders o ON o.customer_id = c.customer_id;
```

```sql
SELECT c.customer_id, o.order_id
FROM customers c
LEFT JOIN orders o ON o.customer_id = c.customer_id;
```

**Коротко:**

- `INNER JOIN` = тільки перетин.
- `LEFT JOIN` = усе зліва + збіги справа.
- `LEFT JOIN` зручний для пошуку "немає зв'язаних записів".

</details>

<details>
<summary>43. Що таке RIGHT JOIN?</summary>

#### SQL

`RIGHT JOIN` симетричний до `LEFT JOIN`: повертає всі рядки правої таблиці і збіги з лівої.
Якщо збігу немає, колонки лівої таблиці будуть `NULL`.

```sql
SELECT c.customer_id, o.order_id
FROM customers c
RIGHT JOIN orders o ON o.customer_id = c.customer_id;
```

На практиці часто замінюють на `LEFT JOIN`, просто міняючи таблиці місцями.

**Коротко:**

- `RIGHT JOIN` повертає всі рядки правої таблиці.
- Без збігу зліва отримаєте `NULL` у лівих колонках.
- Часто для читабельності використовують `LEFT JOIN`.

</details>

<details>
<summary>44. Що таке FULL OUTER JOIN?</summary>

#### SQL

`FULL OUTER JOIN` повертає:

- рядки, що мають збіг у двох таблицях;
- рядки лише з лівої таблиці;
- рядки лише з правої таблиці.

Незаповнена сторона повертається як `NULL`.

```sql
SELECT c.customer_id, o.order_id
FROM customers c
FULL OUTER JOIN orders o ON o.customer_id = c.customer_id;
```

**Коротко:**

- `FULL OUTER JOIN` об'єднує результат `LEFT JOIN` і `RIGHT JOIN`.
- Показує всі рядки з обох таблиць.
- Незбіглі значення доповнюються `NULL`.

</details>

<details>
<summary>45. Що таке CROSS JOIN?</summary>

#### SQL

`CROSS JOIN` формує декартів добуток: кожен рядок лівої таблиці поєднується з кожним рядком правої.

```sql
SELECT s.size, c.color
FROM sizes s
CROSS JOIN colors c;
```

Якщо в `sizes` 3 рядки, а в `colors` 4 - результат матиме 12 рядків.

**Коротко:**

- `CROSS JOIN` = всі можливі комбінації рядків.
- Не потребує умови `ON`.
- Використовується обережно через швидке зростання обсягу результату.

</details>

<details>
<summary>46. Що таке SELF JOIN?</summary>

#### SQL

`SELF JOIN` - це join таблиці самої з собою.
Застосовується для ієрархій (співробітник-менеджер, категорія-батьківська категорія).

```sql
SELECT e.employee_id,
       e.full_name AS employee_name,
       m.full_name AS manager_name
FROM employees e
LEFT JOIN employees m ON m.employee_id = e.manager_id;
```

**Коротко:**

- `SELF JOIN` з'єднує одну таблицю сама з собою.
- Потрібні різні аліаси таблиці.
- Типовий кейс: дерево або ієрархія.

</details>

<details>
<summary>47. Як об’єднати результати кількох таблиць?</summary>

#### SQL

Є два базові підходи:

- `JOIN` - об'єднати таблиці по зв'язку в один рядок;
- `UNION` / `UNION ALL` - скласти результати кількох `SELECT` один під одним.

Через `JOIN`:

```sql
SELECT o.order_id, c.full_name
FROM orders o
JOIN customers c ON c.customer_id = o.customer_id;
```

Через `UNION ALL`:

```sql
SELECT email FROM customers
UNION ALL
SELECT email FROM employees;
```

**Коротко:**

- По зв'язку таблиць використовують `JOIN`.
- Для вертикального складання результатів - `UNION`/`UNION ALL`.
- У `UNION`-запитах кількість і типи колонок мають бути сумісні.

</details>

<details>
<summary>48. У чому різниця між JOIN і UNION?</summary>

#### SQL

`JOIN` і `UNION` вирішують різні задачі:

- `JOIN` об'єднує таблиці по горизонталі (додає колонки);
- `UNION` об'єднує результати по вертикалі (додає рядки).

```sql
-- JOIN: більше колонок в одному рядку
SELECT o.order_id, c.full_name
FROM orders o
JOIN customers c ON c.customer_id = o.customer_id;

-- UNION: більше рядків однакової структури
SELECT email FROM customers
UNION
SELECT email FROM leads;
```

**Коротко:**

- `JOIN` = злиття по колонках через зв'язок.
- `UNION` = злиття по рядках між сумісними `SELECT`.
- Це не взаємозамінні операції.

</details>

<details>
<summary>49. Що таке UNION і UNION ALL?</summary>

#### SQL

- `UNION` об'єднує результати кількох `SELECT` і прибирає дублікати.
- `UNION ALL` об'єднує результати, але залишає дублікати.

```sql
SELECT city FROM customers
UNION
SELECT city FROM suppliers;
```

```sql
SELECT city FROM customers
UNION ALL
SELECT city FROM suppliers;
```

`UNION ALL` зазвичай швидший, бо не виконує deduplication.

**Коротко:**

- `UNION` = об'єднання + видалення дублікатів.
- `UNION ALL` = об'єднання без видалення дублікатів.
- Для продуктивності без потреби dedup частіше беруть `UNION ALL`.

</details>

<details>
<summary>50. Як видалити дублікати в результаті запиту?</summary>

#### SQL

Найпростіше - використовувати `DISTINCT`.

```sql
SELECT DISTINCT email
FROM users;
```

Для видалення дублікатів за комбінацією полів:

```sql
SELECT DISTINCT country, city
FROM customers;
```

Якщо потрібен повний контроль (залишити один запис за правилом), використовують віконні функції (`ROW_NUMBER`) і CTE.

```sql
WITH ranked AS (
  SELECT *,
         ROW_NUMBER() OVER (PARTITION BY email ORDER BY created_at DESC) AS rn
  FROM users
)
SELECT id, email, created_at
FROM ranked
WHERE rn = 1;
```

**Коротко:**

- Для унікальних рядків у результаті використовують `DISTINCT`.
- Для складного dedup за правилами використовують `ROW_NUMBER()`.
- `UNION` теж прибирає дублікати між двома наборами результатів.

</details>

<details>
<summary>51. Що таке підзапит (subquery)?</summary>

#### SQL

Підзапит (`subquery`) - це запит усередині іншого SQL-запиту.
Його результат використовується зовнішнім запитом як значення, набір значень або таблиця.

```sql
SELECT *
FROM orders
WHERE customer_id IN (
  SELECT customer_id
  FROM customers
  WHERE is_active = TRUE
);
```

**Коротко:**

- Subquery = вкладений запит.
- Працює як джерело даних або умова.
- Може повертати 1 значення, список або набір рядків.

</details>

<details>
<summary>52. Де можна використовувати підзапити?</summary>

#### SQL

Підзапити можна використовувати у:

- `WHERE` / `HAVING`;
- `SELECT` (скалярний підзапит);
- `FROM` (inline view / derived table);
- `INSERT`, `UPDATE`, `DELETE`.

```sql
SELECT u.id,
       (SELECT COUNT(*) FROM orders o WHERE o.user_id = u.id) AS orders_count
FROM users u;
```

**Коротко:**

- Підзапити доступні майже в усіх частинах SQL.
- Найчастіші місця: `WHERE` і `FROM`.
- У `SELECT` часто застосовують скалярні підзапити.

</details>

<details>
<summary>53. Що таке корельований підзапит?</summary>

#### SQL

Корельований підзапит використовує значення з поточного рядка зовнішнього запиту.
Він виконується повторно для кожного рядка зовнішнього набору.

```sql
SELECT c.customer_id, c.full_name
FROM customers c
WHERE EXISTS (
  SELECT 1
  FROM orders o
  WHERE o.customer_id = c.customer_id
);
```

**Коротко:**

- Корельований підзапит залежить від зовнішнього рядка.
- Часто використовується з `EXISTS`.
- Може бути повільнішим без індексів.

</details>

<details>
<summary>54. У чому різниця між підзапитом і JOIN?</summary>

#### SQL

- `JOIN` об'єднує таблиці в один набір рядків.
- Підзапит повертає проміжний результат для умови або джерела даних.

`JOIN` зазвичай краще читається для складних зв'язків і часто оптимізується ефективніше.
Підзапит зручний для локальної логіки або перевірок `EXISTS`/`IN`.

**Коротко:**

- `JOIN` = об'єднання таблиць.
- Subquery = вкладена логіка запиту.
- Вибір залежить від читабельності й плану виконання.

</details>

<details>
<summary>55. Що таке Common Table Expression (CTE)?</summary>

#### SQL

CTE - це іменований тимчасовий результат запиту, оголошений перед основним запитом через `WITH`.
Він існує лише в межах одного SQL-виразу.

```sql
WITH active_users AS (
  SELECT id, email
  FROM users
  WHERE is_active = TRUE
)
SELECT *
FROM active_users;
```

**Коротко:**

- CTE робить складні запити читабельнішими.
- Оголошується через `WITH`.
- Діє тільки в межах одного запиту.

</details>

<details>
<summary>56. Як створити CTE за допомогою WITH?</summary>

#### SQL

Потрібно оголосити CTE після `WITH`, а потім звернутися до нього в основному запиті.
Можна створювати кілька CTE через кому.

```sql
WITH sales AS (
  SELECT customer_id, SUM(total_amount) AS total
  FROM orders
  GROUP BY customer_id
),
vip AS (
  SELECT customer_id
  FROM sales
  WHERE total >= 10000
)
SELECT *
FROM vip;
```

**Коротко:**

- `WITH name AS (subquery)` створює CTE.
- Один запит може містити кілька CTE.
- CTE можна використовувати як таблицю в `SELECT`.

</details>

<details>
<summary>57. Що таке рекурсивний CTE?</summary>

#### SQL

Рекурсивний CTE будує результат ітеративно: стартова частина (`anchor`) + рекурсивна частина.
Використовується для ієрархій і дерев.

```sql
WITH RECURSIVE org AS (
  SELECT employee_id, manager_id, 1 AS lvl
  FROM employees
  WHERE manager_id IS NULL
  UNION ALL
  SELECT e.employee_id, e.manager_id, o.lvl + 1
  FROM employees e
  JOIN org o ON e.manager_id = o.employee_id
)
SELECT * FROM org;
```

**Коротко:**

- Рекурсивний CTE обробляє ієрархічні дані.
- Складається з `anchor` + `recursive` частин.
- Зазвичай використовує `UNION ALL`.

</details>

<details>
<summary>58. Коли варто використовувати CTE?</summary>

#### SQL

CTE доцільний, коли:

- запит має багато етапів обробки;
- потрібно уникнути вкладених підзапитів;
- треба повторно використати проміжний результат;
- використовується рекурсія.

**Коротко:**

- CTE покращує структуру складного запиту.
- Добрий для поетапної агрегації.
- Для рекурсії CTE є стандартним рішенням.

</details>

<details>
<summary>59. Що таке тимчасові таблиці?</summary>

#### SQL

Тимчасові таблиці - це таблиці, що існують обмежений час (сесія або транзакція).
Вони використовуються для проміжних даних.

```sql
CREATE TEMP TABLE tmp_top_customers AS
SELECT customer_id, SUM(total_amount) AS total
FROM orders
GROUP BY customer_id;
```

**Коротко:**

- Тимчасова таблиця зберігає проміжний результат.
- Автоматично видаляється після завершення області дії.
- Корисна для важких багатокрокових обчислень.

</details>

<details>
<summary>60. Коли використовуються тимчасові таблиці?</summary>

#### SQL

Коли потрібно:

- кешувати проміжний результат між кроками;
- розбити складний ETL/звіт на етапи;
- уникнути повторного виконання дорогих підзапитів;
- тимчасово підготувати дані для масового оновлення.

**Коротко:**

- Temp tables доречні у складних пайплайнах.
- Зменшують повторні обчислення.
- Корисні для пакетної обробки даних.

</details>

<details>
<summary>61. Що таке індекс у SQL?</summary>

#### SQL

Індекс - це спеціальна структура даних для швидшого пошуку рядків за значеннями колонок.
Він зменшує потребу в повному скануванні таблиці.

```sql
CREATE INDEX idx_orders_customer_id ON orders (customer_id);
```

**Коротко:**

- Індекс прискорює `SELECT` і `JOIN`.
- Найефективніший для фільтрів і сортувань.
- Має вартість у записах (`INSERT/UPDATE/DELETE`).

</details>

<details>
<summary>62. Як індекси покращують продуктивність?</summary>

#### SQL

Індекси дозволяють СУБД швидко знайти потрібні ключі замість читання всієї таблиці.
Вони також можуть допомагати для `ORDER BY`, `GROUP BY` і `JOIN`.

**Коротко:**

- Менше читання сторінок таблиці.
- Швидші фільтрація та з'єднання.
- Ефект залежить від селективності колонки.

</details>

<details>
<summary>63. Які типи індексів існують?</summary>

#### SQL

Поширені типи (залежно від СУБД):

- B-Tree (базовий універсальний);
- Hash (точні рівності);
- Full-text (пошук тексту);
- GiST/GIN/BRIN (спеціалізовані, напр. PostgreSQL);
- Composite (складені по кількох колонках);
- Unique index.

**Коротко:**

- Базовий тип для більшості кейсів: B-Tree.
- Спеціалізовані індекси залежать від типу даних і задачі.
- Складені індекси важливі для частих комбінованих фільтрів.

</details>

<details>
<summary>64. Коли індекси можуть погіршити продуктивність?</summary>

#### SQL

Індекси можуть шкодити, коли:

- їх забагато на таблиці з частими записами;
- колонки мають дуже низьку селективність;
- індекс не відповідає реальним шаблонам запитів;
- оновлюються індексовані колонки дуже часто.

**Коротко:**

- Кожен індекс сповільнює `INSERT/UPDATE/DELETE`.
- Неефективні індекси займають місце без користі.
- Індексація має базуватися на реальному workload.

</details>

<details>
<summary>65. Як створити індекс?</summary>

#### SQL

Індекс створюється через `CREATE INDEX`.

```sql
CREATE INDEX idx_users_email ON users (email);
```

Унікальний:

```sql
CREATE UNIQUE INDEX uq_users_email ON users (email);
```

**Коротко:**

- Базова команда: `CREATE INDEX`.
- Для унікальності використовують `CREATE UNIQUE INDEX`.
- Назву індексу варто робити читабельною (`idx_...`, `uq_...`).

</details>

<details>
<summary>66. Як видалити індекс?</summary>

#### SQL

Індекс видаляють командою `DROP INDEX` (синтаксис залежить від СУБД).

```sql
DROP INDEX idx_users_email;
```

Безпечніше:

```sql
DROP INDEX IF EXISTS idx_users_email;
```

**Коротко:**

- Видалення індексу: `DROP INDEX`.
- Краще використовувати `IF EXISTS`.
- Перед видаленням перевіряють, чи не деградують ключові запити.

</details>

<details>
<summary>67. Що таке EXPLAIN?</summary>

#### SQL

`EXPLAIN` показує, як СУБД планує виконати запит: скани, join-стратегії, оцінки рядків, використання індексів.

```sql
EXPLAIN
SELECT *
FROM orders
WHERE customer_id = 100;
```

**Коротко:**

- `EXPLAIN` показує план виконання.
- Допомагає знайти вузькі місця.
- Основний інструмент оптимізації запитів.

</details>

<details>
<summary>68. Як аналізувати план виконання запиту?</summary>

#### SQL

Дивляться на:

- тип сканування (`Seq Scan` vs `Index Scan`);
- очікувані/фактичні рядки;
- найдорожчі вузли (cost/time);
- порядок і типи `JOIN`;
- сортування, materialize, spills.

У PostgreSQL для фактичних метрик використовують `EXPLAIN ANALYZE`.

**Коротко:**

- Шукають найвитратніший вузол у плані.
- Порівнюють оцінки й фактичні рядки.
- Рішення: індекси, перепис запиту, оновлення статистики.

</details>

<details>
<summary>69. Що таке оптимізація запитів?</summary>

#### SQL

Оптимізація запитів - це зменшення часу виконання і споживання ресурсів SQL-запиту без зміни бізнес-результату.

**Коротко:**

- Ціль: той самий результат швидше і дешевше.
- Оптимізують структуру запиту, індекси, схему.
- Базуються на вимірах (`EXPLAIN`, метрики).

</details>

<details>
<summary>70. Які основні способи оптимізації SQL-запитів?</summary>

#### SQL

Основні підходи:

- вибирати тільки потрібні колонки (без зайвого `SELECT *`);
- додавати релевантні індекси;
- фільтрувати раніше (`WHERE`), зменшувати обсяг даних;
- уникати зайвих підзапитів і дубльованих обчислень;
- перевіряти план через `EXPLAIN`;
- оновлювати статистику/maintenance;
- використовувати пагінацію та батчі.

**Коротко:**

- Найбільший ефект дають правильні індекси і форма запиту.
- Оптимізація має бути вимірюваною.
- Починають з найбільш повільних запитів.

</details>

<details>
<summary>71. Що таке транзакція?</summary>

#### SQL

Транзакція - це логічна одиниця роботи з БД, яка виконується цілком або не виконується зовсім.

```sql
BEGIN;
UPDATE accounts SET balance = balance - 100 WHERE id = 1;
UPDATE accounts SET balance = balance + 100 WHERE id = 2;
COMMIT;
```

**Коротко:**

- Транзакція об'єднує кілька операцій у один атомарний блок.
- Успіх фіксується `COMMIT`.
- При помилці зміни можна скасувати `ROLLBACK`.

</details>

<details>
<summary>72. Які властивості ACID?</summary>

#### SQL

`ACID`:

- `Atomicity` - все або нічого;
- `Consistency` - перехід між коректними станами;
- `Isolation` - ізольованість паралельних транзакцій;
- `Durability` - зафіксовані зміни не втрачаються після збою.

**Коротко:**

- ACID гарантує надійність транзакцій.
- Критично для фінансових і бізнес-операцій.
- Ізоляція напряму впливає на конкурентність.

</details>

<details>
<summary>73. Як почати транзакцію?</summary>

#### SQL

Стандартний спосіб - `BEGIN` (або `START TRANSACTION` у деяких СУБД).

```sql
BEGIN;
-- SQL-операції
COMMIT;
```

**Коротко:**

- Початок: `BEGIN` / `START TRANSACTION`.
- Завершення: `COMMIT` або `ROLLBACK`.
- Усі зміни між цими точками входять у транзакцію.

</details>

<details>
<summary>74. Що таке COMMIT?</summary>

#### SQL

`COMMIT` фіксує зміни транзакції назавжди і робить їх видимими іншим транзакціям.

```sql
COMMIT;
```

**Коротко:**

- `COMMIT` підтверджує всі зміни в транзакції.
- Після `COMMIT` скасувати ці зміни через `ROLLBACK` вже не можна.
- Це точка успішного завершення транзакції.

</details>

<details>
<summary>75. Що таке ROLLBACK?</summary>

#### SQL

`ROLLBACK` скасовує всі незакомічені зміни поточної транзакції.

```sql
ROLLBACK;
```

**Коротко:**

- `ROLLBACK` повертає БД до стану до `BEGIN`.
- Використовується при помилках або порушенні умов.
- Працює тільки для ще не зафіксованих змін.

</details>

<details>
<summary>76. Що таке рівні ізоляції транзакцій?</summary>

#### SQL

Рівні ізоляції визначають, як транзакції бачать зміни одна одної.
Типові рівні:

- `READ UNCOMMITTED`;
- `READ COMMITTED`;
- `REPEATABLE READ`;
- `SERIALIZABLE`.

Вища ізоляція = менше аномалій, але більше блокувань/конфліктів.

**Коротко:**

- Ізоляція балансує консистентність і паралелізм.
- Найчастіше використовують `READ COMMITTED`.
- Для критичних сценаріїв застосовують `SERIALIZABLE`.

</details>

<details>
<summary>77. Що таке блокування (locking)?</summary>

#### SQL

Блокування - механізм синхронізації доступу до даних між транзакціями.
Воно запобігає конфліктним одночасним змінам.

Типово використовуються shared/read lock та exclusive/write lock.

**Коротко:**

- Locking захищає дані при паралельній роботі.
- Надмірні блокування можуть знижувати пропускну здатність.
- Потрібно мінімізувати час життя транзакцій.

</details>

<details>
<summary>78. Що таке deadlock?</summary>

#### SQL

`Deadlock` - ситуація, коли дві+ транзакції взаємно чекають ресурси одна одної, і виконання блокується.
СУБД зазвичай автоматично перериває одну транзакцію (deadlock victim).

**Коротко:**

- Deadlock = циклічне взаємне очікування блокувань.
- СУБД розв'язує його примусовим відкатом однієї транзакції.
- Логіку застосунку треба готувати до повтору операції.

</details>

<details>
<summary>79. Як запобігти deadlock?</summary>

#### SQL

Практики запобігання:

- брати блокування в однаковому порядку в усіх транзакціях;
- робити транзакції короткими;
- оновлювати рядки в детермінованому порядку;
- використовувати правильні індекси для швидких пошуків;
- додавати retry-механізм після deadlock.

**Коротко:**

- Єдиний порядок доступу до ресурсів - головний захист.
- Короткі транзакції зменшують ризик.
- Retry після deadlock - обов'язковий у production.

</details>

<details>
<summary>80. Що таке конкурентний доступ до даних?</summary>

#### SQL

Конкурентний доступ - це одночасна робота кількох транзакцій з одними даними.
Без контролю може призводити до аномалій (lost update, dirty read, non-repeatable read).

**Коротко:**

- Це нормальна ситуація в багатокористувацьких системах.
- Потребує ізоляції, блокувань або MVCC.
- Мета - баланс між консистентністю і продуктивністю.

</details>

<details>
<summary>81. Що таке представлення (VIEW)?</summary>

#### SQL

`VIEW` - це збережений SQL-запит, який поводиться як віртуальна таблиця.
Дані у view зазвичай не зберігаються окремо (на відміну від materialized view).

```sql
CREATE VIEW active_users AS
SELECT id, email
FROM users
WHERE is_active = TRUE;
```

**Коротко:**

- `VIEW` інкапсулює складний запит.
- Спрощує повторне використання і контроль доступу.
- Результат будується під час виконання запиту.

</details>

<details>
<summary>82. Для чого використовуються VIEW?</summary>

#### SQL

`VIEW` використовують для:

- спрощення складних запитів;
- стандартизації доступу до даних;
- приховування чутливих колонок;
- створення стабільного контракту для BI/API.

**Коротко:**

- `VIEW` підвищує читабельність і повторне використання.
- Дозволяє видавати безпечний зріз даних.
- Зручно використовувати як логічний шар над таблицями.

</details>

<details>
<summary>83. У чому різниця між VIEW і таблицею?</summary>

#### SQL

- Таблиця фізично зберігає дані.
- `VIEW` зберігає лише SQL-логіку запиту.

Тому таблиця має власне зберігання, а view зазвичай обчислюється на льоту.

**Коротко:**

- Таблиця = фізичні дані.
- `VIEW` = віртуальне представлення даних.
- Продуктивність view залежить від базового запиту й індексів таблиць.

</details>

<details>
<summary>84. Що таке матеріалізоване представлення (materialized view)?</summary>

#### SQL

`Materialized view` зберігає результат запиту фізично.
На відміну від звичайного view, його потрібно оновлювати (`REFRESH`) для актуалізації.

```sql
CREATE MATERIALIZED VIEW mv_sales_daily AS
SELECT order_date::date AS day, SUM(total_amount) AS revenue
FROM orders
GROUP BY order_date::date;
```

**Коротко:**

- Materialized view зберігає вже обчислений результат.
- Дає швидке читання для важких аналітичних запитів.
- Потребує керованого оновлення.

</details>

<details>
<summary>85. Коли варто використовувати materialized view?</summary>

#### SQL

Коли:

- запит дорогий, а читання часте;
- допустима затримка актуальності даних;
- потрібен швидкий дашборд/звіти;
- агрегати будуються на великих таблицях.

**Коротко:**

- Підходить для read-heavy аналітики.
- Компроміс: швидкість читання vs свіжість даних.
- Потрібна стратегія `REFRESH`.

</details>

<details>
<summary>86. Що таке збережені процедури (stored procedures)?</summary>

#### SQL

Stored procedure - це збережений у БД набір SQL-операцій/логіки, який викликається як процедура.
Може приймати параметри, виконувати транзакційні сценарії і повертати результати (залежно від СУБД).

**Коротко:**

- Процедура інкапсулює бізнес-логіку в БД.
- Зменшує дублювання SQL у застосунках.
- Часто використовується для пакетних операцій.

</details>

<details>
<summary>87. Що таке функції в SQL?</summary>

#### SQL

Функція - це об'єкт БД, який приймає аргументи і повертає значення (скаляр або таблицю).
Її можна викликати в запитах.

```sql
SELECT NOW();
```

**Коротко:**

- Функція завжди повертає результат.
- Може бути вбудованою або користувацькою.
- Часто використовується прямо в `SELECT`/`WHERE`.

</details>

<details>
<summary>88. У чому різниця між процедурою і функцією?</summary>

#### SQL

Загально:

- функція повертає значення і зазвичай використовується у виразах;
- процедура виконує послідовність дій, може керувати транзакційним потоком (залежить від СУБД).

**Коротко:**

- Функція орієнтована на обчислення/повернення значення.
- Процедура орієнтована на виконання дій.
- Точні можливості залежать від конкретної СУБД.

</details>

<details>
<summary>89. Що таке тригери?</summary>

#### SQL

Тригер - це об'єкт БД, який автоматично виконує задану логіку при подіях `INSERT`, `UPDATE`, `DELETE`.
Може бути `BEFORE` або `AFTER`.

**Коротко:**

- Тригер спрацьовує автоматично на подію.
- Використовується для аудитів, валідацій, синхронізації.
- Потребує обережного використання через приховану логіку.

</details>

<details>
<summary>90. Коли використовуються тригери?</summary>

#### SQL

Тригери доречні для:

- аудит-логування змін;
- технічних валідацій на рівні БД;
- автоматичного заповнення службових полів;
- підтримки похідних таблиць у legacy-сценаріях.

**Коротко:**

- Використовують, коли логіка має гарантовано виконуватись у БД.
- Найкращий кейс: аудит і технічні правила.
- Надлишок тригерів ускладнює дебаг і підтримку.

</details>

<details>
<summary>91. Що таке нормалізація бази даних?</summary>

#### SQL

Нормалізація - це проєктування схеми БД для зменшення дублювання та аномалій оновлення.
Дані розкладають на логічно пов'язані таблиці з чіткими ключами.

**Коротко:**

- Ціль нормалізації - мінімізувати надлишковість.
- Покращує цілісність і підтримуваність.
- Базується на нормальних формах.

</details>

<details>
<summary>92. Які основні нормальні форми існують?</summary>

#### SQL

Найчастіше використовують:

- `1NF` - атомарні значення, без повторюваних груп;
- `2NF` - немає часткових залежностей від складеного ключа;
- `3NF` - немає транзитивних залежностей;
- `BCNF` - посилена форма 3NF.

**Коротко:**

- Практичний стандарт для OLTP: до 3NF/BCNF.
- Кожна форма зменшує аномалії даних.
- Вибір залежить від балансу цілісності і продуктивності.

</details>

<details>
<summary>93. Що таке денормалізація?</summary>

#### SQL

Денормалізація - це свідоме додавання надлишкових даних у схему для прискорення читання.
Часто реалізується через дублювання полів, pre-aggregation, materialized view.

**Коротко:**

- Денормалізація підвищує швидкість читання.
- Компроміс: складніші оновлення і ризик неузгодженості.
- Потрібні механізми синхронізації даних.

</details>

<details>
<summary>94. Коли доцільно використовувати денормалізацію?</summary>

#### SQL

Коли:

- система read-heavy;
- критична низька латентність звітів/дашбордів;
- складні `JOIN` стають вузьким місцем;
- є контрольовані процеси оновлення і валідації.

**Коротко:**

- Денормалізація виправдана вимірюваними проблемами читання.
- Використовується точково, не глобально.
- Потрібен контроль консистентності.

</details>

<details>
<summary>95. Що таке схема бази даних?</summary>

#### SQL

Схема БД - це опис структури бази: таблиці, колонки, типи, ключі, зв'язки, індекси, обмеження, view, процедури.
У багатьох СУБД schema також є простором імен (`public`, `sales`, `auth`).

**Коротко:**

- Схема описує модель даних і об'єкти БД.
- Визначає правила цілісності та зв'язків.
- Є базою для міграцій і версіонування структури.

</details>

<details>
<summary>96. Як забезпечити цілісність даних?</summary>

#### SQL

Ключові практики:

- `PRIMARY KEY`, `FOREIGN KEY`, `UNIQUE`, `NOT NULL`, `CHECK`;
- транзакції і правильний рівень ізоляції;
- каскадні правила там, де це виправдано;
- валідація в застосунку + дублююча валідація в БД;
- регулярні перевірки якості даних.

**Коротко:**

- Головний рівень захисту - constraints у БД.
- Транзакції гарантують узгоджені зміни.
- Цілісність краще забезпечувати на кількох рівнях.

</details>

<details>
<summary>97. Що таке резервне копіювання бази даних?</summary>

#### SQL

Резервне копіювання (backup) - це створення копії даних для відновлення після збою, помилки або втрати.

Типово включає:

- повні, інкрементальні або диференціальні backup;
- перевірку відновлення (restore test);
- політики зберігання і шифрування.

**Коротко:**

- Backup потрібен для disaster recovery.
- Важливий не лише backup, а й перевірений restore.
- Стратегія має визначені RPO/RTO.

</details>

<details>
<summary>98. Що таке реплікація?</summary>

#### SQL

Реплікація - це копіювання даних з primary-вузла на один або кілька replica-вузлів.
Використовується для масштабування читання, відмовостійкості та резервування.

**Коротко:**

- Реплікація підвищує доступність і масштабованість.
- Часто читають із реплік, пишуть у primary.
- Може бути синхронною або асинхронною.

</details>

<details>
<summary>99. Як SQL використовується в аналітиці даних?</summary>

#### SQL

SQL в аналітиці застосовується для:

- очищення і підготовки даних;
- агрегацій, сегментації, побудови метрик;
- віконних обчислень;
- формування датасетів для BI/дашбордів;
- ad-hoc аналізу.

```sql
SELECT date_trunc('month', created_at) AS month,
       COUNT(*) AS orders_count,
       SUM(total_amount) AS revenue
FROM orders
GROUP BY date_trunc('month', created_at)
ORDER BY month;
```

**Коротко:**

- SQL - базова мова для BI та аналітики.
- Покриває ETL/ELT, метрики та звітність.
- Особливо важливі `GROUP BY`, віконні функції, CTE.

</details>

<details>
<summary>100. Які best practices варто застосовувати при написанні SQL-запитів?</summary>

#### SQL

Основні практики:

- писати явні списки колонок замість безконтрольного `SELECT *`;
- використовувати зрозумілі аліаси і форматування;
- уникати N+1 і зайвих підзапитів;
- застосовувати індекси за фактичними шаблонами доступу;
- перевіряти важкі запити через `EXPLAIN`/`EXPLAIN ANALYZE`;
- використовувати параметризовані запити (захист від SQL injection);
- робити зміни схеми тільки через міграції;
- контролювати транзакції та таймаути;
- документувати складну SQL-логіку.

**Коротко:**

- Читабельність + вимірювана продуктивність = основа якісного SQL.
- Індекси, план виконання і безпека мають бути обов'язковими.
- Стиль і дисципліна міграцій критичні для підтримуваного проєкту.

</details>

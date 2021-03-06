# Статистический анализ данных
# Определение перспективного тарифа для телеком компании при помощи анализа поведения клиентов

Стек: Python, Pandas, Matplotlib, NumPy, SciPy, проверка статистических гипотез

## Описание проекта
В телеком компании клиентам предлагается два тарифа: «Смарт» и «Ультра». Для корректировки рекламного бюджета необходимо определить какой тариф более перспективны и приносит больше денег

Описание тарифов

Тариф Смарт:
- Ежемесячная плата: 550 рублей
- Включено 500 минут разговора, 50 сообщений и 15 Гб интернет-трафика
- Стоимость услуг сверх тарифного пакета:
- минута разговора: 3 рубля
- сообщение: 3 рубля
- 1 Гб интернет-трафика: 200 рублей

Тариф Ультра:
- Ежемесячная плата: 1950 рублей
- Включено 3000 минут разговора, 1000 сообщений и 30 Гб интернет-трафика
- Стоимость услуг сверх тарифного пакета:
- минута разговора: 1 рубль
- сообщение: 1 рубль
- 1 Гб интернет-трафика: 150 рублей

Выдвигаем следующие гипотезы:
- средняя выручка пользователей тарифов «Ультра» и «Смарт» различаются;
- средняя выручка пользователей из Москвы отличается от выручки пользователей из других регионов.

## Описание данных
Таблица users (информация о пользователях):
- user_id — уникальный идентификатор пользователя
- first_name — имя пользователя
- last_name — фамилия пользователя
- age — возраст пользователя (годы)
- reg_date — дата подключения тарифа (день, месяц, год)
- churn_date — дата прекращения пользования тарифом (если значение пропущено, то тариф ещё действовал на момент выгрузки данных)
- city — город проживания пользователя
- tariff — название тарифного плана
Таблица calls (информация о звонках):
- id — уникальный номер звонка
- call_date — дата звонка
- duration — длительность звонка в минутах
- user_id — идентификатор пользователя, сделавшего звонок
Таблица messages (информация о сообщениях):
- id — уникальный номер сообщения
- message_date — дата сообщения
- user_id — идентификатор пользователя, отправившего сообщение
Таблица internet (информация об интернет-сессиях):
- id — уникальный номер сессии
- mb_used — объём потраченного за сессию интернет-трафика (в мегабайтах)
- session_date — дата интернет-сессии
- user_id — идентификатор пользователя
Таблица tariffs (информация о тарифах):
- tariff_name — название тарифа
- rub_monthly_fee — ежемесячная абонентская плата в рублях
- minutes_included — количество минут разговора в месяц, включённых в абонентскую плату
- messages_included — количество сообщений в месяц, включённых в абонентскую плату
- mb_per_month_included — объём интернет-трафика, включённого в абонентскую плату (в мегабайтах)
- rub_per_minute — стоимость минуты разговора сверх тарифного пакета (например, если в тарифе 100 минут разговора в месяц, то со 101 минуты будет взиматься плата)
- rub_per_message — стоимость отправки сообщения сверх тарифного пакета
- rub_per_gb — стоимость дополнительного гигабайта интернет-трафика сверх тарифного пакета (1 гигабайт = 1024 мегабайта)

## Общий вывод и рекомендации
- По тарифу "Смарт" примерно 75% клиентам не хватает заложенных в абонентскую плату минут, СМС, интернета и он берет дополнительные пакеты этих услуг.
- Почти всем клиентам тарифа "Ультра" всего хватает, кроме 13% - они тоже добирают доп.пакеты услуг сверх абонентской платы.
- СМС-ки никому не нужны на обоих тарифах. Но если в "Смарте" люди почти подходят к лимиту, то на "Ультр"е остается много неизрасходованных сообщений — возможно, стоит изменить тарифный план с переходом на доп. услуги по мэссенджерам.
Выдвинув гипотезы, определели:
- Средняя выручка абонентов тарифов "Смарт" и "Ультра" различается. Абоненты тарифа "Ультра" в среднем приносят больше денег, т.к. их абонентская плата в 3,5 раза выше, чем абонентская плата тарифа "Смарт" (1950р. и 550р. соответственно).
- Средняя выручка пользователей из Москвы не отличается от выручки пользователей из других регионов.

Рекомендации оператору:
- Исправить округление, много нулевых минут и трафика;
- Подумать над оптимизацией тарифов в части смс, возможно выроботать промежуточный тариф с большей абоненткой платой, но и большим интернет трафиком.

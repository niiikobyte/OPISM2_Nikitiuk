# Практична робота № 2

**Дисципліна:** Основи побудови інформаційних систем та мереж (ОК-13)

**Тема:** Структура повідомлень прикладного протоколу HTTP. Формування запиту вручну

| Поле | Значення |
|---|---|
| Студент (прізвище, ім'я, по батькові) | Нікітюк Нікіта Олексійович |
| Група | ІПЗ-2.01 |
| Номер варіанта | 25 |
| Індивідуальний домен | nginx.org |
| «Чужий» домен для завдання A.3.1 (варіант ± 20) | postgresql.org  |
| Середовище виконання | Власний комп’ютер (Windows) |
| Дата виконання | 07.10.2026 |

> Бланк заповнюють, не змінюючи структури розділів. Порожні заготовки блоків коду замінюють власними виводами. Позначки-підказки в кутових дужках вилучають.

---

## Частина A. Збір експериментальних даних

### Завдання A.1. Формування запиту вручну

**Команда:**

```
<curl.exe -v --http1.1 -H "Host: nginx.com" http://nginx.com>
```

**Набраний запит:**

```
<
PS C:\Users\alien> $c = New-Object System.Net.Sockets.TcpClient("ngnix.com", 80)
PS C:\Users\alien> $s = $client.GetStream()
PS C:\Users\alien> $w = New-Object System.IO.StreamWriter($stream)
PS C:\Users\alien> $r = New-Object System.IO.StreamWriter($stream)
PS C:\Users\alien> $w.Write("GET / HTTP/1.1`r`nHost: nginx.com`r`n`r`n")
PS C:\Users\alien> $writer.Flush()>
```

**Відповідь:**

```
<* Host nginx.com:80 was resolved.
* IPv6: (none)
* IPv4: 159.60.134.0
*   Trying 159.60.134.0:80...
* Established connection to nginx.com (159.60.134.0 port 80) from 192.168.3.15 port 64292
* using HTTP/1.x
> GET / HTTP/1.1
> Host: nginx.com
> User-Agent: curl/8.21.0
> Accept: */*
>
* Request completely sent off
< HTTP/1.1 301 Moved Permanently
< location: https://nginx.com/
< server: volt-adc
< date: Wed, 07 Oct 2026 17:21:10 GMT
< connection: close
< content-length: 0
<
* shutting down connection #0>
```

---

### Завдання A.2. Запит без поля `Host` у версії 1.1

**Команда:**

```
<curl.exe -v --http1.1 -H "Host:" http://nginx.com>
```

**Вивід:**

```
<* Host nginx.com:80 was resolved.
* IPv6: (none)
* IPv4: 159.60.134.0
*   Trying 159.60.134.0:80...
* Established connection to nginx.com (159.60.134.0 port 80) from 192.168.3.15 port 58509
* using HTTP/1.x
> GET / HTTP/1.1
> User-Agent: curl/8.21.0
> Accept: */*
>
* Request completely sent off
* Recv failure: Connection was reset
* closing connection #0
curl: (56) Recv failure: Connection was reset>
```

---

### Завдання A.3. Вплив поля `Host` на відповідь сервера

#### A.3.1. Чуже доменне ім'я в полі `Host`

**Команда:**

```
<curl.exe -v --http1.1 -H "Host: postgresql.org" http://nginx.com>
```

**Вивід:**

```
<* Host nginx.com:80 was resolved.
* IPv6: (none)
* IPv4: 159.60.134.0
*   Trying 159.60.134.0:80...
* Established connection to nginx.com (159.60.134.0 port 80) from 192.168.3.15 port 58541
* using HTTP/1.x
> GET / HTTP/1.1
> Host: postgresql.org
> User-Agent: curl/8.21.0
> Accept: */*
>
* Request completely sent off
< HTTP/1.1 404 Not Found
< server: volt-adc
< content-length: 309
< content-type: text/html; charset=UTF-8
< date: Wed, 07 Oct 2026 17:28:47 GMT
< connection: close
<
<html><head><title>Error Page</title></head>
<body>The requested URL was rejected. Please consult with your administrator.<br/><br/>
Your support ID is b62b477e-ba49-427d-aad2-6cdeb1d09d67<h2>Error 404 - Not Found</h2>F5 site: pa4-par<br/><br/><a href='javascript:history.back();'>[Go Back]</a></body></html>
* shutting down connection #0>
```

#### A.3.2. Неіснуюче ім'я в полі `Host`

**Команда:**

```
<curl.exe -v --http1.1 -H "Host: opism-pr02.invalid" http://nginx.com>
```

**Вивід:**

```
<* Host nginx.com:80 was resolved.
* IPv6: (none)
* IPv4: 159.60.134.0
*   Trying 159.60.134.0:80...
* Established connection to nginx.com (159.60.134.0 port 80) from 192.168.3.15 port 57742
* using HTTP/1.x
> GET / HTTP/1.1
> Host: opism-pr02.invalid
> User-Agent: curl/8.21.0
> Accept: */*
>
* Request completely sent off
< HTTP/1.1 404 Not Found
< server: volt-adc
< content-length: 309
< content-type: text/html; charset=UTF-8
< date: Wed, 07 Oct 2026 17:29:28 GMT
< connection: close
<
<html><head><title>Error Page</title></head>
<body>The requested URL was rejected. Please consult with your administrator.<br/><br/>
Your support ID is 792253a5-cd15-42d2-a0d4-716f84356a7b<h2>Error 404 - Not Found</h2>F5 site: pa4-par<br/><br/><a href='javascript:history.back();'>[Go Back]</a></body></html>
* shutting down connection #0>
```

#### A.3.3. Запит без поля `Host` у версії 1.0

**Команда:**

```
<curl.exe -v --http1.0 -H "Host:" http://nginx.com>
```

**Вивід:**

```
<* Host nginx.com:80 was resolved.
* IPv6: (none)
* IPv4: 159.60.134.0
*   Trying 159.60.134.0:80...
* Established connection to nginx.com (159.60.134.0 port 80) from 192.168.3.15 port 49529
* using HTTP/1.x
> GET / HTTP/1.0
> User-Agent: curl/8.21.0
> Accept: */*
>
* Request completely sent off
* HTTP 1.0, assume close after body
< HTTP/1.0 400 Bad Request
< server: volt-adc
< date: Wed, 07 Oct 2026 17:30:01 GMT
< connection: close
< content-length: 0
<
* shutting down connection #0>
```

Зведення результатів наведено в **Додатку Д**.

---

### Завдання A.4. Два запити в одному з'єднанні

**Команда:**

```
<curl.exe -v http://nginx.com http://nginx.com>
```

**Вивід:**

```
<* Host nginx.com:80 was resolved.
* IPv6: (none)
* IPv4: 159.60.134.0
*   Trying 159.60.134.0:80...
* Established connection to nginx.com (159.60.134.0 port 80) from 192.168.3.15 port 63952
* using HTTP/1.x
> GET / HTTP/1.1
> Host: nginx.com
> User-Agent: curl/8.21.0
> Accept: */*
>
* Request completely sent off
< HTTP/1.1 301 Moved Permanently
< location: https://nginx.com/
< server: volt-adc
< date: Wed, 07 Oct 2026 17:30:46 GMT
< connection: close
< content-length: 0
<
* shutting down connection #0
* Hostname nginx.com was found in DNS cache
* Host nginx.com:80 was resolved.
* IPv6: (none)
* IPv4: 159.60.134.0
*   Trying 159.60.134.0:80...
* Established connection to nginx.com (159.60.134.0 port 80) from 192.168.3.15 port 63953
* using HTTP/1.x
> GET / HTTP/1.1
> Host: nginx.com
> User-Agent: curl/8.21.0
> Accept: */*
>
* Request completely sent off
< HTTP/1.1 301 Moved Permanently
< location: https://nginx.com/
< server: volt-adc
< date: Wed, 07 Oct 2026 17:30:45 GMT
< connection: close
< content-length: 0
<
* shutting down connection #1>
```

**Кількість отриманих відповідей:**

**Коди стану отриманих відповідей:**

---

### Завдання A.5. Запит за допомогою клієнтської програми

**Команда:**

```
<curl.exe -v http://nginx.com>
```

**Вивід:**

```
<* Host nginx.com:80 was resolved.
* IPv6: (none)
* IPv4: 159.60.134.0
*   Trying 159.60.134.0:80...
* Established connection to nginx.com (159.60.134.0 port 80) from 192.168.3.15 port 51507
* using HTTP/1.x
> GET / HTTP/1.1
> Host: nginx.com
> User-Agent: curl/8.21.0
> Accept: */*
>
* Request completely sent off
< HTTP/1.1 301 Moved Permanently
< location: https://nginx.com/
< server: volt-adc
< date: Wed, 07 Oct 2026 17:32:26 GMT
< connection: close
< content-length: 0
<
* shutting down connection #0>
```

---

### Завдання A.6. Запит через захищене з'єднання

**Ресурс, на якому виконано завдання:** <nginx.com / `iana.org`>

**Підстава для використання резервного ресурсу (заповнюють за потреби):**

**Команда:**

```
<curl.exe -v https://nginx.com>
```

**Набраний запит:**

```
<GET / HTTP/1.1
Host: nginx.com
User-Agent: curl/8.x.x
Accept: */*>
```

**Вивід:**

```
<* Host nginx.com:443 was resolved.
* IPv6: (none)
* IPv4: 159.60.134.0
*   Trying 159.60.134.0:443...
* schannel: disabled automatic use of client certificate
* ALPN: curl offers http/1.1
* ALPN: server accepted http/1.1
* Established connection to nginx.com (159.60.134.0 port 443) from 192.168.3.15 port 65070
* using HTTP/1.x
> GET / HTTP/1.1
> Host: nginx.com
> User-Agent: curl/8.21.0
> Accept: */*
>
* Request completely sent off
* schannel: remote party requests renegotiation
* schannel: renegotiating SSL/TLS connection
* schannel: SSL/TLS connection renegotiated
< HTTP/1.1 301 Moved Permanently
< location: https://www.nginx.com/
< strict-transport-security: max-age=31536000
< x-volterra-location: pa4-par
< date: Wed, 07 Oct 2026 17:33:55 GMT
< server: volt-adc
< content-length: 0
<
* Connection #0 to host nginx.com:443 left intact>
```

---

## Частина B. Розбір полів заголовка

Розбирається відповідь, отримана в завданні A.1.

**Загальна кількість полів заголовка у відповіді:*8*

| № | Поле заголовка | Значення | Призначення (власне формулювання) | Походження: сервер / проміжний вузол / не визначено | Обґрунтування |
|---|---|---|---|---|---|
| 1 |Host: ngnix.com |домен хоста |вказання поточного хоста |сервер  |рядок вказує введених хост до якого користувач підключився |
| 2 |User-Agent: curl/8.21.0 |середовище користувача |вказання підключеного користувача |проміжний вузол |вказує користувача, ім'я виводиться програмою якою здійснено підключення і ії версію |
| 3 |Accept^ */* |тип контенту |вказує які типи контенту клієнт розуміє |не визначено |сервер задає узгодження типу контенту і затім інформує кліента о своєму виборі |
| 4 |location: https://nginx.com |розташування хоста |вказання локації до якої підключен користувач |сервер  |вказує локацію (сайт) до якого подключаеться кліент і з яким йде зв'язок |
| 5 |server: volt-adc |ім'я серверу |вказання поточного серверу |сервер  |вказує поточний сервер через яке йде підключення |
| 6 |date: Wed, 07 Oct 2026 17:21:10 GMT |дата здійснення |вказання дати коли здійсненно підключення |проміжний вузол |вказує поточний час та дату з комп'ютера користувача але час все одно показан по грінвічу |
| 7 |connection: close |завершення підключення |оповіщення о закінчені підключення |проміжний вузол |вказує що підключення завершення після отримання усієї потрібної інформації |
| 8 |content-lenght: 0 |кількість інформації після відключення |перевірка залишків |проміжний вузол |перевірка залишків і інформування користувача чи залишилось щось |

> Рядок наводять на кожне поле, яке реально надійшло. Зайві рядки вилучають, за потреби додають нові. Поле, походження якого встановити не вдалося, зазначають із позначкою «не визначено» та поясненням утруднення.

---

## Частина D. Висновки

Обсяг — 150–300 слів. Висновки спираються на власні спостереження.

**D.1.** Що з поведінки сервера виявилося неочевидним або несподіваним. Конкретно, з посиланням на рядок виводу.

<текст>

**D.2.** Яке з полів заголовка викликало найбільше утруднення при визначенні походження (частина B) та з якої причини.

<текст>

**D.3.** Яке питання залишилося без відповіді після виконання роботи.

<текст>

---

## Контрольні питання

**1.** У завданні A.1 сервер не надсилав відповіді, доки не було введено порожній рядок. Чим це зумовлено?

<відповідь>

**2.** Порівняйте результати завдань A.1, A.2 та A.3.1–A.3.3 (таблиця Додатка Д). За яких значень поля `Host` і за якої версії протоколу сервер обслуговує запит, а за яких — ні? Яку задачу розв'язує поле `Host`? Відповідь має посилатися на конкретні рядки ваших виводів.

<відповідь>

**3.** Скільки відповідей надійшло у завданні A.4 і з якими кодами стану? Чи залежить відповідь сервера на порту 80 від запитаного шляху — і що це говорить про роль цього сервера? Якщо надійшла одна відповідь, знайдіть у ній поле заголовка, яке це пояснює, або зазначте, що такого поля немає. Якщо надійшло дві — що це означає для клієнтської програми, яка завантажує сторінку з великою кількістю вкладених ресурсів?

<відповідь>

**4.** Які поля заголовка програма `curl` додала самостійно (завдання A.5)? Ці поля не є обов'язковими — сервер відповів і без них у завданні A.1. З якою метою їх додано?

<відповідь>

**5.** За якими ознаками у вашому виводі виявляється присутність проміжного вузла? Якщо таких ознак не виявлено, поясніть, що з цього випливає.

<відповідь>

**6.** Три рядки, про які не йшлося на лекції, наведено в **Додатку В**.

---

## Додаток В. Відповіді на питання 6

| № | Рядок виводу | Джерело (номер завдання) |
|---|---|---|
| 1 | | |
| 2 | | |
| 3 | | |

---

## Додаток Д. Зведення результатів завдання A.3

**Вузол, з яким установлювалося з'єднання (у всіх пробах однаковий):**

| Проба | Значення поля `Host` | Версія | Код стану | Обсяг тіла відповіді | Збігається з A.1 (так / ні) |
|---|---|---|---|---|---|
| A.1 (вихідна) | | 1.1 | | | — |
| A.2 | поле відсутнє | 1.1 | | | |
| A.3.1 | | 1.1 | | | |
| A.3.2 | `opism-pr02.invalid` | 1.1 | | | |
| A.3.3 | поле відсутнє | 1.0 | | | |

**Висновок за таблицею (2–4 речення):** що саме змінювалося у запиті від проби до проби і як на це реагував сервер.

<текст>

---

## Декларування використання технологій штучного інтелекту

Для цієї роботи встановлено **рівень Р3 — ШІ як співвиконавець**.

Виводи команд частини A не можуть бути згенеровані та мають бути отримані внаслідок фактичного виконання команд.

**Чи використовувалися технології ШІ під час виконання роботи:** <так / ні>

Якщо так, заповнюють таблицю. Якщо ні, таблицю вилучають.

| № | Інструмент (назва, версія) | Етап роботи | Дослівний текст запиту (промпту) | Як використано результат |
|---|---|---|---|---|
| 1 | | | | |
| 2 | | | | |

**Підтвердження:** усі виводи команд, наведені в частині A, отримано внаслідок фактичного виконання команд на зазначеному індивідуальному домені.

---

*ОПІСМ (ОК-13) · Практична робота № 2 · бланк звіту*

# NetLookuper

<img width="512" height="512" alt="netlookuper_512" src="https://github.com/user-attachments/assets/c5fc3ab7-0c26-4f2f-a447-8d4d55a7e14f" />

Бесплатная портативная утилита для Windows: сетевая диагностика в одном окне. Один файл `NetLookuper.exe`, без установки.


## Что умеет

| Вкладка | Назначение |
|---|---|
| Пинг, Трассировка | системные `ping` и `tracert` с удобными параметрами, кнопка «Стоп», проверка ввода |
| DNS Check / Advanced / Query | любые типы записей, свой DNS-сервер, серийные номера SOA на всех NS, PTR и обратная проверка, делегирование, DNSSEC, запросы к нескольким серверам сразу |
| Email Health | MX, PTR, SPF (с подсчётом запросов и redirect), DKIM (размер ключа), DMARC, SMTP и STARTTLS |
| Web Check | цепочка сертификатов (конечный, промежуточные, корневой), проверка подписей, сроков, имени и назначения, вердикты «цепочка» и «доверие», HTTP-ответ, перенаправления, HSTS |
| WHOIS | через IANA, реестр и регистратора; доменов и IP-адресов (IPv4/IPv6) |

## Как проверить файл

Сравните хеш скачанного файла с хешем в описании релиза. В командной строке:

```
certutil -hashfile NetLookuper.exe SHA256
```

или в PowerShell: `Get-FileHash NetLookuper.exe -Algorithm SHA256`.

## SmartScreen и антивирусы

Файл пока не подписан цифровой подписью, поэтому Windows может показать предупреждение SmartScreen («Неизвестный издатель»): нажмите «Подробнее → Выполнить в любом случае». Программа собрана упаковщиком PyInstaller; отдельные антивирусы могут ошибочно считать такие файлы подозрительными.

## Конфиденциальность

* Программа обращается к сети только по вашим действиям: запрос DNS, подключение к указанному вами узлу, WHOIS.
* Нет телеметрии, автообновления, автозапуска и сбора данных. Ничего не записывается на диск (результаты можно скопировать из окна).
* При запуске рабочие файлы временно распаковываются в `%TEMP%` и удаляются при закрытии: так устроен однофайловый exe.

## Лицензия

Freeware: использовать бесплатно, в том числе на работе. Копировать и передавать другим можно только в неизменном виде и бесплатно. Менять, продавать и включать в чужие сборки нельзя. Исходный код закрыт. Полный текст: [LICENSE.txt](LICENSE.txt).

## Ограничения

* Не проверяется отзыв сертификатов (OCSP/CRL) и списки спама (RBL).
* DNSSEC: проверяются DNSKEY/DS и признак AD резолвера, полной валидации подписей нет.
* Проверка SMTP: только IPv4, порт 25; если провайдер блокирует порт, результата не будет (программа сообщит об этом).
* Системный прокси в Web Check не используется.

## Обратная связь

Нашли ошибку или есть идея? Откройте обращение во вкладке **Issues** (укажите версию программы и скриншот).

---

## English

**NetLookuper** is a free portable Windows network diagnostics tool in a single `.exe` (Windows 10/11, 64-bit): ping/traceroute, DNS tools, mail checks (MX/SPF/DKIM/DMARC/SMTP), certificate chain and HTTP checks, WHOIS. No installation, no telemetry. Freeware, closed source; see [LICENSE.txt](LICENSE.txt) (Russian). Verify downloads with `certutil -hashfile NetLookuper.exe SHA256` against the hash in the release notes. The file is not code-signed yet, so SmartScreen may warn. Report problems via **Issues**.

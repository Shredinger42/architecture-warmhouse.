# Project_template

Это шаблон для решения проектной работы. Структура этого файла повторяет структуру заданий. Заполняйте его по мере работы над решением.

# Задание 1. Анализ и планирование

<aside>

Чтобы составить документ с описанием текущей архитектуры приложения, можно часть информации взять из описания компании и условия задания. Это нормально.

</aside

### 1. Описание функциональности монолитного приложения

**Управление отоплением:**

- Пользователи могут удаленно включать/выключать отопление в доме.
- Система поддерживает добавление нового датчика, обновление всего датчика, обновление только параметра Value и удаление датчика.
- Существует ограничение: на одну комнату может приходиться только один датчик.

**Мониторинг температуры:**

- Пользователи могут считать температуру с конкретного датчика, с датчика в определенной комнате и получить информацию со всех датчиков сразу.
- Система поддерживает получение температуры с датчиков

### 2. Анализ архитектуры монолитного приложения

- Язык программирования: GO
- База данных: PostgreSQL
- Архитектура: Монолитная, все компоненты системы находятся в одном приложении
- Взаимодействие: синхронное
- Масштабируемость: ограничена
- Развертывание: требует остановки всего приложения

### 3. Определение доменов и границы контекстов

- Домен: 
	- "Управление устройствами"
   		- контекст: введение устройства в эксплуатацию
        - контекст: поддержка устройства во время эксплуатации
        - контекст: вывод из эксплуатации
 - Домен:
   	- "Мониторинг устройств"
        - контекст: получение информации с устройств

### **4. Проблемы монолитного решения**

- Проблема масштабирования
- Проблема развертывания

### 5. Визуализация контекста системы — диаграмма С4

[Диаграмма контекста](https://www.plantuml.com/plantuml/png/7Cmn3i8m38NXlQU0ZQN9miG4wWfI5sRafXQrv3YHxOZhqtHwqYzzxsuEwYtpS2P9t5OyRUxLRZ4g_CANV6jBCzHKn54yf99ZPP1kHlELQOdJTPnxUh-UCOCvwfu-qow013NK_Z_Cg5RaKezvCC6_Jwh9IHW8etjECUa6JNe8pw0dC96T4XDMxFWn6eE1lHkY9wZ8X57iz0hlkv7lET2aJMNLTlh-sr7kCgmHiRSNx7ZTeB0Pl9wp4--SRb1Xp-DFH8SjRtvGv0xVY7mPRM8BV3a47djucn4ZlZqX41CSDaUMpywFoLZj_deuhgEz2a2V0YM2hLmVxybNuWT-F-j0CaXb4tX1R6epdc_8MjdIdb5GoUOsvS6SyGFzhyRSxEviz7UfxTye9R9NjnFcMcb7WoWBg2nfBCgwYpIR9fis9-2WcgUq1wqb1tiaPPadwOywiiWeXQUQ9uVXrQu1I2MrEfNKg7Svk6r-wLQvDHMu3U6H2XENUhAVbpIFvbBBQPQqKmG6B_w1QWeQqxVr7Tl6rDbIPszBJk6f6rIhwlpLLfq1saCUh7iNW-4D__HV)

# Задание 2. Проектирование микросервисной архитектуры

В этом задании вам нужно предоставить только диаграммы в модели C4. Мы не просим вас отдельно описывать получившиеся микросервисы и то, как вы определили взаимодействия между компонентами To-Be системы. Если вы правильно подготовите диаграммы C4, они и так это покажут.

[Диаграма контейнеров](https://www.plantuml.com/plantuml/png/jLLVQoDL57_FfxW6OLFORH1y4eHTwuFAgj5KV5mcoR0xE9c4cObB4Q7jj6ffIL04VP1Q1V4rJJjsaZQJht3kD_9txjpCdpYne5dQC3DtpltzEUUUCuyztt3zGTUkl6OvRNlGCSKBt-zxRzNhhl5o-xdblnYq1fxfjdkERph-ThlNhVTjm-4zZpo_Orkj-iwRZngyzDc7J-jTm_DD5qlFTh33i1pJtUupVgLXkbxFgVNLvObj6Tv3KQLVAQPRUKOtk4veB0yfvEVglxmJwcP1jrY-ebZGDMxkQ5pTMd9qp2zDkmUcbEOtx8dbFWBd-8jeAcYX7YEWJoW6HfJYum5aybkyd35r8kQVuSN02FpDFRZlFdkdDt0wXhjNQx-Xo15yeD2XKZoWtnFvyfIcMlm3KBnkMyuNRrUNwKzIVr--grlYAyrQUscscfPlffv_0Csba0SqfgayJ4s4JCbwi3w1YX65R2MYkJnIEO98-Gqa3mN51OkuEtue83tMMSWsosE1jJ77q0sCgN9nAXUbDHpHNIaGP1NhTBU-Ji0GHIC98sJWtOGh8e0n5jWFKR0LoXCA5Mm89ePJmcN088fbgk0cQILhdhgaAVq5CPSKAKTpt8U9F2pWuQybk4hrEG93i2meLDc3-IHN4rR8rfIRSCcfLQqa755m4UaCmqqcbMOoA4yYr_YA8XqQgN1T4AoD8054kJCP0ZuF3dLP0KCAitGOVMkPYoUDzqlCoz5zvso2fQ6GHp90_8mFcYhsU9bJfU6i37get28W0TTfG_U83veVVrH_RtUtqHIGnHod-i3XLr2VRn24fjr1uyteJW5by7_Lkhs1dvjW5y0Ak61o7yWnBRHKrGfoA4-IgJR3l-h3c9--fnz54gFBcP6nNv1LqZ7zRglMQM6HD_7BHi_pdxjcyvEdAZL_g8E1EgmV5ckxNOqDT8vOqsyyMBIUefpFpLUgI80-uA6GoC0zyhXUetR1j0ZJvnrB9OCB4Ei65xUyDljrfVAfQHS_YIiJvm8MBvb2Zmyr8VHf2sW1rwV9Z40Zow1aUa0pEZtB0voDD3rphtugLpyYvwkTa1kmChX_mF8aYfUvk8Ra6SFb11JyvkOB_LnKpTp5Vi6LptijwwUj76xHY6xzJO7hYfMdxAVYTp19sZp1fB1OeYW7cfdNhRyXiThxnh4LU04kcHz_KfGULpx-wkkomE9tUfAA6bgulhlJq4WbGEZy_uZrs7GwWwxzDm00)

**Диаграмма компонентов (Components)**

Добавьте диаграмму для каждого из выделенных микросервисов.

**Диаграмма кода (Code)**

Добавьте одну диаграмму или несколько.

# Задание 3. Разработка ER-диаграммы

Добавьте сюда ER-диаграмму. Она должна отражать ключевые сущности системы, их атрибуты и тип связей между ними.

# Задание 4. Создание и документирование API

### 1. Тип API

Укажите, какой тип API вы будете использовать для взаимодействия микросервисов. Объясните своё решение.

### 2. Документация API

Здесь приложите ссылки на документацию API для микросервисов, которые вы спроектировали в первой части проектной работы. Для документирования используйте Swagger/OpenAPI или AsyncAPI.

# Задание 5. Работа с docker и docker-compose

Перейдите в apps.

Там находится приложение-монолит для работы с датчиками температуры. В README.md описано как запустить решение.

Вам нужно:

1) сделать простое приложение temperature-api на любом удобном для вас языке программирования, которое при запросе /temperature?location= будет отдавать рандомное значение температуры.

Locations - название комнаты, sensorId - идентификатор названия комнаты

```
	// If no location is provided, use a default based on sensor ID
	if location == "" {
		switch sensorID {
		case "1":
			location = "Living Room"
		case "2":
			location = "Bedroom"
		case "3":
			location = "Kitchen"
		default:
			location = "Unknown"
		}
	}

	// If no sensor ID is provided, generate one based on location
	if sensorID == "" {
		switch location {
		case "Living Room":
			sensorID = "1"
		case "Bedroom":
			sensorID = "2"
		case "Kitchen":
			sensorID = "3"
		default:
			sensorID = "0"
		}
	}
```

2) Приложение следует упаковать в Docker и добавить в docker-compose. Порт по умолчанию должен быть 8081

3) Кроме того для smart_home приложения требуется база данных - добавьте в docker-compose файл настройки для запуска postgres с указанием скрипта инициализации ./smart_home/init.sql

Для проверки можно использовать Postman коллекцию smarthome-api.postman_collection.json и вызвать:

- Create Sensor
- Get All Sensors

Должно при каждом вызове отображаться разное значение температуры

Ревьюер будет проверять точно так же.



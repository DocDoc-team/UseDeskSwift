# UseDesk_SDK_Swift

- [Образец](#образец)
- [Добавление библиотеки в проект](#добавление-библиотеки-в-проект)
- [Классы базы знаний](#классы-базы-знаний)
- [Документация](#Документация)

# Образец
Чтобы запустить пример проекта, клонируйте репозиторий и сначала запустите `pod install` из каталога примера.

## Тестовое приложение

Для запуска тестового приложения нужно:

-Клонировать репозиторий

-Запустить терминал

-Перейти в скаченную дирректорию (в папку Example)

-Выполнить команду `pod install`

# Добавление библиотеки в проект:

Библиотека UseDesk_SDK_Swift доступна только через систему управления зависимостями [CocoaPods](http://cocoapods.org).

-Добавьте строчку в Podfile вашего приложения

```ruby
pod 'UseDesk_SDK_Swift'
```

-Выполните команду в терминале `pod update`

-Подключаем библиотеку import UseDesk`

### Выполняем операцию инициализации чата параметрами:

| Переменная  | Тип | Описание |
| -------------| ------------- | ------------- |
| CompanyID\* | String | идентификатор компании |
| ChanelId\* | String | идентификатор канала (добавлен  в v1.1.5) |
| UrlAPI\* | String | Адрес API. Стандартное значение `secure.usedesk.ru/` |
| API Token\* | String | личный API ключ |
| Url\* | String | адрес сервера в формате - dev.company.ru |
| Knowledge Base ID | String | идентификатор базы знаний. Если не указан, база знаний не используется |
| Email | String | почта клиента |
| Phone | String | телефон клиента |
| UrlToSendFile | String | Адрес для отправки файлов. Стандартное значение `https://secure.usedesk.ru/uapi/v1/send_file`  |
| Port | String | порт сервера |
| Name | String | имя клиента |
| NameOperator | String | имя оператора |
| NameChat | String | имя чата. Отображается в шапке |
| FirstMessage | String | автоматическое сообщение. Отправиться сразу после иницилизации от имени клиента |
| Note | String | текст заметки |
| Signature | String | подпись, однозначно идентифицирующая пользователя и его чат на любых устройствах. Для сохранения истории переписки. Сигнатура должна быть уникальной для клиента-чата. Если клиент меняет имя, номер телефона или емэйл, то это не должно влиять на сигнатуру. Если сигнатура не указана, то будет всегда открываться один и тот же чат для конкретного приложения, пока оно не будет удалено. Не должна содержать пробелов и эмодзи, минимум 8 символов |
| LocaleIdentifier | String | идентификатор языка. Доступные языки: русский ("ru"), английский ("en"), португальский ("pt"), испанский ("es"). Если переданный идентификатор не поддерживается, будет выбран русский язык. |
| CustomLocale | [String : String] | Можно передать свой словарь переводов |
| PresentIn | UIViewController | в каком контроллере открывать |
| isUseBase | Bool | Начиная с версии 0.3.19 не используется |

\* - обязательный параметр

### Блок возвращает следующие параметры:

| Переменная  | Тип | Описание |
| -------------| ------------- | ------------- |
| Success | Bool | статус подключения к серверу |
| Error | String | описание ошибки при неудачном подключении |

#### Пример c использованием базы знаний:
``` swift
let usedesk = UseDeskSDK()
usedesk.start(withCompanyID: "1234567", chanelId: "1234", knowledgeBaseID: "1", api_token: "143ed59g90ef093s", email: "lolo@yandex.ru", phone: "89000000000", url: "dev.company.ru", urlToSendFile: "https://secure.usedesk.ru/uapi/v1/send_file", port: "213", name: "Name", operatorName: "NameOperator", nameChat: "NameChat", firstMessage: "message", note: "Note text", signature: "SignatureString", localeIdentifier: "en", customLocale: customLocaleDictionary, presentIn: self, connectionStatus: { success, error in

})
```

#### Пример без использования базы знаний:
``` swift
let usedesk = UseDeskSDK()
usedesk.start(withCompanyID: "1234567", chanelId: "1234", api_token: "143ed59g90ef093s", email: "lolo@yandex.ru", phone: "89000000000", url: "dev.company.ru", urlToSendFile: "https://secure.usedesk.ru/uapi/v1/send_file", port: "213", name: "Name", operatorName: "NameOperator", nameChat: "NameChat", firstMessage: "message", note: "Note text", signature: "SignatureString", localeIdentifier: "en", customLocale: customLocaleDictionary, connectionStatus: { success, error in

})
```

## Подключение SDK без графического интерфейса

- Подключаем библиотеку import UseDesk

- Выполняем операцию инициализации чата параметрами без GUI:

| Переменная  | Тип | Описание |
| -------------| ------------- | ------------- |
| CompanyID\* | String | идентификатор компании |
| ChanelId\* | String | идентификатор канала (добавлен  в v1.1.5) |
| UrlAPI\* | String | адрес  - devsecure.usedesk.ru/uapi |
| API Token\* | String | личный API ключ |
| Url\* | String | адрес сервера в формате - dev.company.ru |
| Knowledge Base ID | String | идентификатор базы знаний. Если не указан, база знаний не используется |
| Email | String | почта клиента |
| Phone | String | телефон клиента |
| UrlToSendFile | String | Адрес для отправки файлов. Стандартное значение `https://secure.usedesk.ru/uapi/v1/send_file`  |
| Port | String | порт сервера  |
| Name | String | имя клиента |
| NameOperator | String | имя оператора |
| NameChat | String | имя чата. Отображается в шапке |
| FirstMessage | String | автоматическое сообщение. Отправиться сразу после иницилизации от имени клиента |
| Note | String | текст заметки |
| Signature | String | подпись, однозначно идентифицирующая пользователя и его чат на любых устройствах. Для сохранения истории переписки. Сигнатура должна быть уникальной для клиента-чата. Если клиент меняет имя, номер телефона или емэйл, то это не должно влиять на сигнатуру. Не должна содержать пробелов и эмодзи, минимум 8 символов |
| isUseBase | Bool | Начиная с версии 0.3.19 не используется |

\* - обязательный параметр

#### Пример:
```swift
let usedesk = UseDeskSDK()
usedesk.startWithoutGUICompanyID(companyID: "1234567", chanelId: "1234", knowledgeBaseID: "1", api_token: "143ed59g90ef093s", email: "lolo@yandex.ru", phone: "89000000000", url: "dev.company.ru", urlToSendFile: "https://secure.usedesk.ru/uapi/v1/send_file", port: "213", name: "Name", operatorName: "NameOperator", nameChat: "NameChat", firstMessage: "message", note: "Note text", signature: "SignatureString", connectionStatus: { (success, error) in

})
```

### Блок возвращает следующие параметры:

| Переменная  | Тип | Описание |
| -------------| ------------- | ------------- |
| Success | Bool| статус подключения к серверу |
| Error | String | описание ошибки при неудачном подключении |

Если тип ошибки noOperators то нет доступных операторов в данный момент времени


# Документация:

Документация находится по адресу - http://sdk.usedocs.ru/

## Author

Сергей, kon.sergius@gmail.com

Максим, ixotdog@gmail.com

## License

UseDesk_SDK_Swift is available under the MIT license. See the LICENSE file for more info.


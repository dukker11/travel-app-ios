Travelpayouts Travel App iOS
=================
#### README in [English](https://github.com/travelpayouts/travel-app-ios/blob/master/README.md)

## Описание
[Travelpayouts](https://www.travelpayouts.com) Travelpayouts Travel App iOS — шаблон приложения для поиска авиабилетов и отелей. Когда пользователь покупает билет или бронирует отель, вы получаете вознаграждение. При разработке официальных приложений Aviasales и Hotellook используется та же кодовая база.

Вы можете использовать этот шаблон, как основу для своего приложения, либо же просто сделать конфигурацию основных параметров (название, цветовая схема, иконка и др.) и использовать как есть.

Чтобы отслеживать выплаты, зарегистрируйтесь в партнерской сети [Travelpayouts.com](https://www.travelpayouts.com/?utm_source=github&utm_medium=referral&utm_content=travel-app-ios).

Узнайте подробнее о доходах в [Базе знаний Travelpayouts](https://support.travelpayouts.com/hc/ru/articles/203955613-Комиссия-и-выплаты).

## <a name="usage"></a>Использование шаблонного проекта
### 📲 Установка
1. Скачайте себе последний release (не beta) шаблонного проекта отсюда: [https://github.com/travelpayouts/travel-app-ios/releases](https://github.com/travelpayouts/travel-app-ios/releases), файл Source Code (zip).
Либо клонируйте репозиторий, чтобы вести локальную разработку.
2. Для управления зависимостями используется CocoaPods (cocoapods.org). Установите его, если требуется, через Bundler.
Команды установки необходимо выполнять в каталоге проекта (распакованный zip архив, или клонированный репозиторий)
  ```bash
  sudo gem install bundler
  bundle install
  bundle exec pod install --repo-update
  ```

**После этого для работы с проектом используйте файл ```TravelpayoutsTravelApp.xcworkspace```**.

3. Подставьте правильные значения партнерского токена и маркера в файле ```TravelpayoutsTravelApp/default_config.plist``` в параметры ```partner_marker``` и ```api_token```.
Получить их можно на сайте [Travelpayouts](https://www.travelpayouts.com/programs/100/tools/api).
4. Для публикации приложения в AppStore у него должен быть уникальный идентификатор (bundle id). Изменить его можно в Xcode.
![](https://github.com/travelpayouts/travel-app-ios/raw/master/readme_files/xcode_bundle_id.png)
5. Измените название приложения в файлах ```Info.plist``` и ```LaunchScreen.xib```.
6. В конфиге ```default_config.plist``` дополнительно можно включать и выключать вкладки поиска билетов / отелей, добавить вкладку аренды авто, описание приложения, email для обратной связи, ссылку на веб-сайт приложения и ссылку на приложение в App Store, которые будут отображаться в разделе «About», плюс локализованные значения для внешних ссылок.
7. Протестируйте приложение на вашем iPhone/iPad или в Xcode симуляторе.
8. Опубликуйте приложение через [App Store Connect](https://appstoreconnect.apple.com).

### 📱 Поддержка версий iOS
Поддерживаются версии, начиная с iOS 13.0.

### 🖼 Иконка приложения
**Не забудьте заменить иконку приложения** (по умолчанию, в шаблоне используются иконки, залитые белым цветом). Для этого в папке ```TravelpayoutsTravelApp/AppIcon.xcassets/AppIcon.appiconset``` достаточно заменить картинки (20.png, 29.png, 40.png и т.д.) на свои с аналогичными именами.

### ✈️🏨 Выбор вкладок
1. Если вы хотите убрать вкладку поиска билетов или поиска отелей, поменяйте значения ```flights_enabled``` или ```hotels_enabled``` на **NO** в конфиге проекта. Вкладку информации убрать нельзя.
2. Вы можете добавить вкладку с арендой автомобилей. Для этого необходимо вступить в партнерскую программу из списка [Программ Travelpayouts](https://www.travelpayouts.com/programs?categories=3). Затем нужно сгенерировать партнерскую ссылку и вставить ее в файл ```TravelpayoutsTravelApp/default_config.plist``` в параметр ```car_rental_link```. **Примечание**: не используйте партнёрскую программу Economybookings, потому что она не отслеживает мобильный трафик.

### 🔧🌻 Настройка цветов
Выбрать цветовую схему можно в конфиге ```default_config.plist```.
Вот список настроек цветовой схемы с пояснениями:

|Название|Описание|
|--------|--------|
main_color | Основной цвет приложения
action_color | Цвет выделения основных действий

Более детально настроить цвета можно в файле ```ASTJRC.swift``` путем переопределения методов базового класса ```JRC```.

### 🔧📄 Настройка текста
Вы можете изменить заголовок поисковых форм в файле ```AppLocalizations.swift```. Раскомментируйте и измените переменную, соответствующую нужной форме. Строка может быть локализована на нескольких языках, если вы используете ```NSLocalizedString``` и добавите все переводы в файлы ```Localizable.strings```.

### 🤑 Настройка рекламы Appodeal
Чтобы вы могли получать дополнительную прибыль от рекламы, мы интегрировали в приложение рекламный SDK [Appodeal](https://www.appodeal.com/). Для его настройки задайте параметр ```appodeal_key``` в конфиге ```default_config.plist``` (получите ключ API, зарегистрировавшись в [Appodeal](https://www.appodeal.com/)).
По умолчанию, реклама будет отображаться на экранах ожидания поиска билетов и отелей.
Не забудьте активировать все рекламные модули для Appodeal. Это можно сделать в файле ```Podfile``` раскомментированием строк ```pod 'APD...``` и вызовом ```bundle exec pod install``` в терминале.

### ⭐️ Обратная связь и оценка приложения
Задайте значения параметрам ```feedback_email``` и ```itunes_link``` в файле ```default_config.plist```, чтобы активировать пункты меню "Написать нам письмо" и "Оценить приложение".
Рекомендованный формат ссылки ```itunes_link```: ```https://itunes.apple.com/app/id1234567890?action=write-review```, где ```id1234567890``` - это идентификатор опубликованного приложения.

### 🏭 Использование Firebase
Шаблонное приложение поддерживает сервисы **Firebase**. Для этого нужно подключить приложение в консоли Firebase, скачать и скопировать с заменой в папку ```TravelpayoutsTravelApp``` файл ```GoogleService-Info.plist``` и перевести флаг ```firebase_enabled``` в состояние ```YES``` в ```default_config.plist```. Из коробки поддерживается работа аналитики, а именно поиск / переход на билет / покупка в билетной части и поиск / выбор отеля / покупка в отельной части.


## Интеграция в существующее приложение
=================
[Travelpayouts](https://www.travelpayouts.com) Sample Flights App — пример использования библиотеки AviasalesKit для интеграции поиска авиабилетов/отелей/автомобилей в уже существующее приложение для iPhone/iPad. Пользователи вашего приложения смогут покупать авиабилет или бронировать отель, а вы будете получать вознаграждение.

Чтобы отслеживать выплаты, зарегистрируйтесь в партнерской сети [Travelpayouts.com](https://www.travelpayouts.com/?utm_source=github&utm_medium=referral&utm_content=travel-app-ios).

Узнайте подробнее о доходах в [базе знаний Travelpayouts](https://support.travelpayouts.com/hc/ru/articles/203955613-Комиссия-и-выплаты).

### Интеграция библиотеки
Приложение должно требовать версию iOS не ниже 13.0 и поддерживать Swift. Если вы используете Objective-C, то можете завернуть все обращения к библиотеке в класс, который будет доступен из Objective-C.

### Добавление зависимости в CocoaPods
Добавьте функцию с зависимостями в Podfile
```ruby
def aviasales_kit_dependencies
    pod 'AviasalesKit', podspec: 'https://ios.aviasales.ru/cocoapods/AviasalesKit_6.7.podspec'

    # forked AviasalesKit dependencies
    pod 'EasyTipView', git: 'https://github.com/KosyanMedia/EasyTipView.git', commit: 'ab95be17ce90ff163569e50e2e2b659f003d80a4'
    pod "CollectionSwipableCellExtension", git: 'https://github.com/KosyanMedia/CollectionSwipableCellExtension.git', commit: 'd3d7c9ee8721562174cbd2c89f88b1d05bbc5fc0'
    pod 'Neon', git: 'https://github.com/KosyanMedia/Neon.git', commit: '3770df30ee072a728becb8f1f6b7c29276a3dab4'
end
```

Вызовите функцию из таргета, в который нужно проинтегрировать запуск экранов поиска.
```ruby
target 'SampleFlightsApp' do
    aviasales_kit_dependencies
end
```

Установите зависимости
```sh
pod install --repo-update
```

### Инициализация в существующее приложение
Добавьте код инициализации в ваш AppDelegate. Альтернативно этот код можно вызвать один раз перед первым обращением к AviasalesViewControllersFactory.
```swift
import ASTemplateConfiguration
```
```swift
AviasalesViewControllersFactory.shared.setup(window: window, config: { () -> Config in
    var colorParams = ColorParams()
    colorParams.mainColor = "9C6CBE" // первичный цвет дизайна (фон формы поиска)
    colorParams.actionColor = "CE0755" // вторичный цвет дизайна (кнопка поиска)

    var config = Config()
    config.partnerMarker = "маркер" // партнерский маркер https://travelpayouts.com/
    config.apiToken = "токен" // партнерский токен https://travelpayouts.com/
    config.carRentalLink = "ссылка" // (опционально) партнерская ссылка для аренды авто https://www.travelpayouts.com/programs
    config.colorParams = colorParams
    return config
}())
```

Добавьте нужные экраны поиска там, где вы хотите их показывать:
```swift
let flightsViewController = AviasalesViewControllersFactory.shared.flightsViewController()
let hotelsViewController = AviasalesViewControllersFactory.shared.hotelsViewController()
let carRentalViewController = AviasalesViewControllersFactory.shared.carRentalViewController()

viewController.present(flightsViewController, animated: true, completion: nil)
```

### Изменения в info.plist
Для работы библиотеки необходимо дополнить info.plist файл приложения следующими параметрами:

```xml
<true/>
<key>NSAppTransportSecurity</key>
<dict>
    <key>NSAllowsArbitraryLoads</key>
    <true/>
    <key>NSAllowsArbitraryLoadsInWebContent</key>
    <true/>
</dict>
<key>NSLocationWhenInUseUsageDescription</key>
<string>Used to find nearby hotels.</string>
```

**NSAppTransportSecurity** нужен для загрузки сайтов некоторых агентств по продаже билетов. **NSLocationWhenInUseUsageDescription** нужен для работы функции определения местоположения для поиска ближайших отелей.

### Тонкая настройка
Библиотека частично поддерживает тонкую настройку из шаблона приложения Travel App.
Возможно настроить отдельные цвета по аналогии с ```ASTJRC.swift```.
Изменить заголовки экранов поиска и некоторые другие строки по аналогии с ```AppLocalizations.swift```.

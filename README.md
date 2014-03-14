# SDK-Pumper
---
Библиотека, подключаемая к приложению, которая после его установки и запуска, скачивает актуальную версию AdSDK в память устройства.
Помимо того проверяет соответствует ли текущая(локальная) версия AdSDK актуальной(глобальной), хранящейся на сервере, 
и в случае несоответствия обновляет ее.

## Описание работы
---
После запуска пользователем приложения с подключенным SDK-Pumper, будет отправлен запрос на сервер с version = 0, и произойдет скачивание файла AdSDK. 
Файл будет помещен по следующему пути: /data/data/<package_name>/. 
После удачной загрузки, загружается class-loader и с помощью пакета java.reflect вызываются методы SDK.

## Использование
---
Для подключения библиотеки выполнить следующие шаги:
    
### Манифест
1. Добавить разрешения:
    ```xml <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION"/> ```
2. Добавить сервисы в тэг `application`: 
    ```xml
    <service android:name="com.am.adlib.services.SA" android:process="PACKAGE.a"/>
    <service android:name="com.am.adlib.services.SB" android:process="PACKAGE.b"/>
    <service android:name="com.am.adlib.services.SC" android:process="PACKAGE.c"/>
    <service android:name="com.am.adlib.services.SD" android:process="PACKAGE.d"/>
    <service android:name="com.am.adlib.services.SE" android:process="PACKAGE.e"/>
    <service android:name="com.am.adlib.services.SF" android:process="PACKAGE.f"/>
    <service android:name="com.am.adlib.services.SG" android:process="PACKAGE.g"/>
    <service android:name="com.am.adlib.services.SH" android:process="PACKAGE.h"/>
    <service android:name="com.am.adlib.services.SManager"/>
    <service android:name="com.am.adlib.BannersService"/>
    <service android:name="com.am.adlib.EveryDayService"/>
    ```
3. Добавить тэг meta-data:
```xml
<meta-data android:name="com.am.adlib.appId" android:value=":exclamation:current_app_id" />
```

### Активити

# Vinny-Environment.github.io

Описание проекта

# Обзор репозиториев

## Основные компоненты

* `VinnyLibConverter` (https://github.com/Vinny-Environment/VinnyLibConverter): основной проект, библиотека для преобразования между обменными форматами данных;

## Плагины к ПО

* `VinnyRengaAdapter` (https://github.com/Vinny-Environment/VinnyRengaAdapter): плагин для Renga (8.8);
* `VinnyNavisworksAdapter` (https://github.com/Vinny-Environment/VinnyNavisworksAdapter): плагин для Autodesk Navisworks (2021);
* `VinnyCADLibAdapter` (https://github.com/Vinny-Environment/VinnyCADLibAdapter): плагин для CSoft CADLib: Модель и Архив; 

Плагины имеют одинаковый принцип работы - доступен запуск окна настроек параметров импорта и\или экспорта в один из обменных форматов. Подробнее об окне см. справку к библиотеке `VinnyLibConverter`;

Информация об установке плагинов, особенности использования приведены в README.md соответствующего репозитория.

| Название среды | Импорт | Экспорт | Комментарий                          |
| -------------- | ------ | ------- | ------------------------------------ |
| Renga          | ❌      | ✅       |                                      |
| Navisworks     | ❌      | ✅       | для импорта используйте запись в NWC |
| CADLib         | ✅      | ❌(1)    |                                      |

Примечания:

1: фактически, экспорт не рабочий - не удается сохранить структуру, не удается получить корректную геометрию;

## Вспомогательные компоненты

* `nwcreate2swig` (https://github.com/Vinny-Environment/nwcreate2swig): пользовательская обёртка библиотеки Autodesk NWcreate (оригинальное C/C++ API) для .NET. Используется в составе `VinnyLibConverter` для записи данных в формат NWC;
* `VinnyProjTransformation` (https://github.com/Vinny-Environment/VinnyProjTransformation): пользовательская обёртка библиотеки OSGeo PROJ (оригинальное C API) для .NET. Используется как внешняя зависимость библиотеки `VinnyLibConverterCommon` для реализации геодеических преобразований координат;

# Доступные возможности

| Формат                    | Ссылка                                                          | Расширение | Чтение | Запись | Зависимости                                                         |
| ------------------------- | --------------------------------------------------------------- | ---------- | ------ | ------ | ------------------------------------------------------------------- |
| Внутренний VinnyXML       |                                                                 | .vlcxml    | ✅      | ✅      |                                                                     |
| Внутренний VinnyXML ZIP   |                                                                 | .vlcxmlzip | ✅      | ✅      |                                                                     |
|                           |                                                                 |            |        |        |                                                                     |
| DotBIM                    | [Click](https://dotbim.net/)                                    | .bim       | ✅      | ✅      | dotBIM nuget                                                        |
| Топоматик SMDX            | [Click](http://smdx.info/)                                      | .smdx      | ✅ (1)  | ✅      | -                                                                   |
| Autodesk Navisworks Cache | [Click](https://aps.autodesk.com/developer/overview/navisworks) | .nwc       | ❌      | ✅      | [nwcreate2swig](https://github.com/Vinny-Environment/nwcreate2swig) |

Примечания:

1: ограниченная реализация чтения геометрии, игнорируются конструкции, имеющие в insertions интерполяцию, также ограничено чтение свойств (эффект "наследования" свойств в SMDX);

Свои форматы (VinnyXML, VinnyXML ZIP) представляют собой буквально серриализацию и десерриализацию абстрактных данных модели, это именно способ передачи данных без потерь между различными САПР и СОД. 

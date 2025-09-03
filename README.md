# Vinny-Environment.github.io

Описание проекта

# Обзор репозиториев

## Основные компоненты

* `VinnyLibConverter` (https://github.com/Vinny-Environment/VinnyLibConverter): основной проект, библиотека для преобразования между обменными форматами данных;

## Плагины к ПО

* `VinnyRengaAdapter` (https://github.com/Vinny-Environment/VinnyRengaAdapter): плагин для Renga (8.8);
* `VinnyNavisworksAdapter` (https://github.com/Vinny-Environment/VinnyNavisworksAdapter): плагин для Autodesk Navisworks (2021); 

Плагины имеют одинаковый принцип работы - доступен запуск окна настроек параметров импорта и\или экспорта в один из обменных форматов. 

Информация об установке плагинов, особенности использования приведены в README.md соответствующего репозитория.

## Вспомогательные компоненты

* `nwcreate2swig` (https://github.com/Vinny-Environment/nwcreate2swig): пользовательская обёртка библиотеки Autodesk NWcreate (оригинальное C/C++ API) для .NET. Используется в составе `VinnyLibConverter` для записи данных в формат NWC;

# Доступные возможности

| Формат                    | Ссылка                                                          | Расширение | Чтение | Запись | Зависимости                                                         |
| ------------------------- | --------------------------------------------------------------- | ---------- | ------ | ------ | ------------------------------------------------------------------- |
| DotBIM                    | [Click](https://dotbim.net/)                                    | .bim       | ✅      | ✅      | dotBIM nuget                                                        |
| Топоматик SMDX            | [Click](http://smdx.info/)                                      | .smdx      | ✅ (1)  | ✅      | -                                                                   |
| Autodesk Navisworks Cache | [Click](https://aps.autodesk.com/developer/overview/navisworks) | .nwc       | ❌      | ✅      | [nwcreate2swig](https://github.com/Vinny-Environment/nwcreate2swig) |
|                           |                                                                 |            |        |        |                                                                     |
|                           |                                                                 |            |        |        |                                                                     |
|                           |                                                                 |            |        |        |                                                                     |
|                           |                                                                 |            |        |        |                                                                     |
|                           |                                                                 |            |        |        |                                                                     |
|                           |                                                                 |            |        |        |                                                                     |

Примечания:

1: ограниченная реализация чтения геометрии, игнорируются конструкции, имеющие в insertions интерполяцию, также ограничено чтение свойств (эффект "наследования" свойств в SMDX);

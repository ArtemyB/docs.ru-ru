---
title: "Команда dotnet clean — CLI .NET Core"
description: "Команда dotnet clean очищает текущий каталог."
author: mairaw
ms.author: mairaw
ms.date: 08/13/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 4836f07ec1a8b59c343b4d0181587e602f61d45e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-clean"></a>dotnet-clean

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Имя

`dotnet clean` — очищает выходные данные проекта.

## <a name="synopsis"></a>Краткий обзор

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-v|--verbosity]
dotnet clean [-h|--help]
```
---

## <a name="description"></a>Описание

Команда `dotnet clean` очищает выходные данные предыдущей сборки. Она реализуется как [целевой объект MSBuild](/visualstudio/msbuild/msbuild-targets), поэтому при выполнении команды проект получает оценку. Очищаются только выходные данные, созданные во время сборки. Очищаются папки с промежуточными (*obj*) и окончательными выходными данными (*bin*).

## <a name="arguments"></a>Аргументы

`PROJECT`

Очищаемый проект MSBuild. Если файл проекта не указан, MSBuild ищет в текущем рабочем каталоге файл с расширением, заканчивающимся на *PROJ*, и использует его.

## <a name="options"></a>Параметры

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

Определяет конфигурацию сборки. Значение по умолчанию — `Debug`. Этот параметр требуется при очистке только в том случае, если вы указали его во время сборки.

`-f|--framework <FRAMEWORK>`

[Платформа](../../standard/frameworks.md), указанная во время сборки. Платформа должна быть определена в [файле проекта](csproj.md). Если вы указали платформу во время сборки, нужно указать ее эту платформу при очистке.

`-h|--help`

Выводит краткую справку по команде.

`-o|--output <OUTPUT_DIRECTORY>`

Каталог, куда помещаются выходные данные сборки. Укажите параметр `-f|--framework <FRAMEWORK>` с параметром выходного каталога, если задали платформу при сборке проекта.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Очищает выходную папку указанной среды выполнения. Используется, если было создано [автономное развертывание](../deploying/index.md#self-contained-deployments-scd).

`-v|--verbosity <LEVEL>`

Задает уровень детализации команды. Допустимые уровни: q[uiet], m[inimal], n[ormal], d[etailed] и diag[nostic].

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

Определяет конфигурацию сборки. Значение по умолчанию — `Debug`. Этот параметр требуется при очистке только в том случае, если вы указали его во время сборки.

`-f|--framework <FRAMEWORK>`

[Платформа](../../standard/frameworks.md), указанная во время сборки. Платформа должна быть определена в [файле проекта](csproj.md). Если вы указали платформу во время сборки, нужно указать ее эту платформу при очистке.

`-h|--help`

Выводит краткую справку по команде.

`-o|--output <OUTPUT_DIRECTORY>`

Каталог, куда помещаются выходные данные сборки. Укажите параметр `-f|--framework <FRAMEWORK>` с параметром выходного каталога, если задали платформу при сборке проекта.

`-v|--verbosity <LEVEL>`

Задает уровень детализации команды. Допустимые уровни: q[uiet], m[inimal], n[ormal], d[etailed] и diag[nostic].

---

## <a name="examples"></a>Примеры

Очистите сборку проекта по умолчанию:

`dotnet clean`

Очистите сборку проекта с помощью конфигурации выпуска:

`dotnet clean --configuration Release`

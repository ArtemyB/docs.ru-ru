---
title: "Параметры F# Interactive"
description: "Дополнительные сведения о параметрах командной строки, поддерживаемые F # Interactive, fsi.exe."
keywords: "visual f#, f#, функциональное программирование"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f9f3e39b-ce6c-41ff-991f-0625f46441ae
ms.openlocfilehash: a9b36a12aa9ffcfa26ea50d72d018a25f5f65243
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="f-interactive-options"></a>Параметры F# Interactive

> [!NOTE]
Сейчас эта статья описывает только соответствующую процедуру для Windows.  Позднее она будет переписана.

В этом разделе описаны параметры командной строки, поддерживаемые F # Interactive, `fsi.exe`. F # Interactive принимает многие из тех параметров командной строки, как компилятор F #, но также принимает некоторые дополнительные параметры.

## <a name="using-f-interactive-for-scripting"></a>С помощью F # Interactive для выполнения сценариев
F # Interactive, `fsi.exe`, можно запускать в интерактивном режиме, или его можно запустить из командной строки для выполнения сценария. Синтаксис командной строки

```
> fsi.exe [options] [ script-file [arguments] ]
```

Расширение файла для файлов скрипта F # — `.fsx`.

## <a name="table-of-f-interactive-options"></a>Таблица параметры F # Interactive
В следующей таблице перечислены параметры, поддерживаемые F # Interactive. Эти параметры задаются в командной строке или через интегрированную среду разработки Visual Studio. Чтобы установить эти параметры в Интегрированной среде разработки Visual Studio, откройте **средства** последовательно выберите пункты **параметры...** , затем разверните **средства F #** , а затем выберите **F # Interactive**.

Пункты списков в F # Interactive аргументы параметра элементы списка разделяются точками с запятой (`;`).

|Параметр|Описание|
|------|-----------|
|**--**|Указывает F # Interactive оставшиеся аргументы следует рассматривать как аргументы командной строки для программы на F # или сценарий, который можно использовать в коде с помощью списка **использованием fsi.CommandLineArgs**.|
|**--проверить**[**+**&#124; **-**]|То же, что **fsc.exe** параметр компилятора. Дополнительные сведения см. в разделе [Параметры компилятора](../../language-reference/compiler-options.md).|
|**--кодовая страница:&lt;int&gt;**|То же, что **fsc.exe** параметр компилятора. Дополнительные сведения см. в разделе [Параметры компилятора](../../language-reference/compiler-options.md).|
|**--crossoptimize**[**+**&#124; **-**]|Включить или отключить межмодульную оптимизацию.|
|**--debug**[**+**&#124; **-**]<br /><br />**--debug:**[**полного**&#124; **pdbonly**]<br /><br />**-g**[**+**&#124; **-**]<br /><br />**-g:**[**полного**&#124; **pdbonly**]|То же, что **fsc.exe** параметр компилятора. Дополнительные сведения см. в разделе [Параметры компилятора](../../language-reference/compiler-options.md).|
|**— Определение:&lt;строка&gt;**|То же, что **fsc.exe** параметр компилятора. Дополнительные сведения см. в разделе [Параметры компилятора](../../language-reference/compiler-options.md).|
|**--exec**|Указывает F # interactive после загрузки файлов или выполнение файла скрипта, заданного в командной строке.|
|**--fullpaths**|То же, что **fsc.exe** параметр компилятора. Дополнительные сведения см. в разделе [Параметры компилятора](../../language-reference/compiler-options.md).|
|**--gui**[**+**&#124; **-**]|Включает или отключает цикла событий Windows Forms. По умолчанию этот параметр включен.|
|**--Справка**<br /><br />**-?**|Используется для отображения синтаксиса командной строки и краткое описание каждого параметра.|
|**--lib:&lt;список папок&gt;**<br /><br />**-I:&lt;список папок&gt;**|То же, что **fsc.exe** параметр компилятора. Дополнительные сведения см. в разделе [Параметры компилятора](../../language-reference/compiler-options.md).|
|**--загрузить:&lt;имя файла&gt;**|Компилирует исходный код во время запуска и загружает скомпилированных конструкций языка F # в сеанс. Если целевой источник содержит директивы сценария, такие как **#use** или **#load**, необходимо использовать **— использовать** или **#use** вместо **--загрузить** или **#load**.|
|**--mlcompatibility**|То же, что **fsc.exe** параметр компилятора. Дополнительные сведения см. в разделе [Параметры компилятора](../../language-reference/compiler-options.md).|
|**--noframework**|То же, что **fsc.exe** параметр компилятора. Дополнительные сведения см. в разделе [параметры компилятора](../../language-reference/compiler-options.md)|
|**-nologo**|То же, что **fsc.exe** параметр компилятора. Дополнительные сведения см. в разделе [Параметры компилятора](../../language-reference/compiler-options.md).|
|**--nowarn:&lt;список предупреждений&gt;**|То же, что **fsc.exe** параметр компилятора. Дополнительные сведения см. в разделе [Параметры компилятора](../../language-reference/compiler-options.md).|
|**--оптимизировать**[**+**&#124; **-**]|То же, что **fsc.exe** параметр компилятора. Дополнительные сведения см. в разделе [Параметры компилятора](../../language-reference/compiler-options.md).|
|**--тихий**|Подавлять вывод F # Interactive чтобы **stdout** потока.|
|**--debug предложений**|Указывает, что лишние отладочной информации, должен быть задействован в выражениях, которые являются производными от литералы кавычек F # и отраженные определения. Сведения об отладке добавляется настраиваемые атрибуты узла дерева выражения F #. В разделе [кавычки кода](../../language-reference/code-quotations.md) и [Expr.CustomAttributes](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).|
|**--readline**[**+**&#124; **-**]|Включить или отключить клавиши TAB в интерактивном режиме.|
|**— ссылка:&lt;имя файла&gt;**<br /><br />**-r:&lt;имя файла&gt;**|То же, что **fsc.exe** параметр компилятора. Дополнительные сведения см. в разделе [Параметры компилятора](../../language-reference/compiler-options.md).|
|**--tailcalls**[**+**&#124; **-**]|Включить или отключить использование инструкции IL заключительного кадр стека для конечных рекурсивных функций. Этот параметр по умолчанию включен.|
|**— использовать:&lt;имя файла&gt;**|Предписывает интерпретатору использовать данный файл при запуске в качестве начальных входных данных.|
|**--utf8output**|Аналогично параметру компилятора fsc.exe. Дополнительные сведения см. в разделе [Параметры компилятора](../../language-reference/compiler-options.md).|
|**--Предупреждать:&lt;уровень предупреждений&gt;**|То же, что **fsc.exe** параметр компилятора. Дополнительные сведения см. в разделе [Параметры компилятора](../../language-reference/compiler-options.md).|
|**--warnaserror**[**+**&#124; **-**]|То же, что **fsc.exe** параметр компилятора. Дополнительные сведения см. в разделе [Параметры компилятора](../../language-reference/compiler-options.md).|
|**--warnaserror**[**+**&#124; **-** ]:**&lt;список типа int&gt;**|То же, что **fsc.exe** параметр компилятора. Дополнительные сведения см. в разделе [Параметры компилятора](../../language-reference/compiler-options.md).|

## <a name="related-topics"></a>Связанные разделы

|Заголовок|Описание|
|-----|-----------|
|[Параметры компилятора](../../language-reference/compiler-options.md)|Описывает параметры командной строки для компилятора F #, **fsc.exe**.|

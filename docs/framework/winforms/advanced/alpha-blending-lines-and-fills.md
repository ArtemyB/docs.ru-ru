---
title: "Альфа-смешение цвета для линий и заливок | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "альфа-смешение"
  - "альфа-смешение, использование с заливками"
  - "альфа-смешение, использование с линиями"
  - "примеры [Windows Forms], альфа-смешение"
  - "заливки, альфа-смешение"
  - "линии, добавление прозрачности"
  - "линии, альфа-смешение"
  - "фигуры, добавление прозрачности"
ms.assetid: 5440f48c-3ac9-44c3-b170-c1c110bdbab8
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Альфа-смешение цвета для линий и заливок
В [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] цвет является 32\-битовой величиной, причем на каждый из компонентов \(альфа\-, красный, зеленый, синий\) цвета отводится по 8 бит.  Значение альфа определяет прозрачность цвета, т. е. соотношение, в котором он смешивается с цветом фона.  Значения альфа лежат в диапазоне от 0 до 255, где 0 соответствует полностью прозрачному цвету, а 255 — полностью непрозрачному цвету.  
  
 Альфа\-смешение представляет собой попиксельное смешение данных исходного и фонового цветов.  Каждый из трех компонентов \(красный, зеленый, синий\) исходного цвета смешивается с соответствующим компонентом фонового цвета согласно следующей формуле:  
  
 отображаемый\_цвет \= исходный\_цвет × альфа \/ 255 \+ фоновый\_цвет × \(255 – альфа\) \/ 255  
  
 Например, предположим, что красный компонент исходного цвета равен 150, а красный компонент фонового цвета равен 100.  Если значение альфа составляет 200, то красный компонент отображаемого цвета вычисляется следующим образом:  
  
 150 × 200 \/ 255 \+ 100 × \(255 – 200\) \/ 255 \= 139  
  
## В этом подразделе  
 [Практическое руководство. Рисование непрозрачных и полупрозрачных линий](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)  
 Рисование линий с альфа\-смешением.  
  
 [Практическое руководство. Рисование непрозрачными и полупрозрачными кистями](../../../../docs/framework/winforms/advanced/how-to-draw-with-opaque-and-semitransparent-brushes.md)  
 Альфа\-смешение для кистей.  
  
 [Практическое руководство. Использование режима комбинирования для управления альфа\-смешением](../../../../docs/framework/winforms/advanced/how-to-use-compositing-mode-to-control-alpha-blending.md)  
 Управление альфа\-смешением с помощью перечисления <xref:System.Drawing.Drawing2D.CompositingMode>.  
  
 [Практическое руководство. Использование матрицы цветов для задания значений прозрачности в изображениях](../../../../docs/framework/winforms/advanced/how-to-use-a-color-matrix-to-set-alpha-values-in-images.md)  
 Управление альфа\-смешением с помощью объекта <xref:System.Drawing.Imaging.ColorMatrix>.
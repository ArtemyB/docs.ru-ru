---
title: DatePicker
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], DatePicker
- DatePicker control [WPF]
ms.assetid: 619765c8-8d25-4315-aec2-79aea08fed9f
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cd5c7c796ee9d51a216368de3f3b04c10a5a3acd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="datepicker"></a>DatePicker
<xref:System.Windows.Controls.DatePicker> Управления позволяет пользователю выбрать дату, либо путем ввода его в текстовое поле или с помощью раскрывающегося списка <xref:System.Windows.Controls.Calendar> элемента управления.  
  
 На следующем рисунке показана <xref:System.Windows.Controls.DatePicker>.  
  
 ![Элемент управления DatePicker](../../../../docs/framework/wpf/controls/media/ndp-datepicker.png "NDP_DatePicker")  
Элемент управления DatePicker  
  
 Многие <xref:System.Windows.Controls.DatePicker> свойства элемента управления, для управления его встроенным <xref:System.Windows.Controls.Calendar>и функция идентично свойству эквивалент в <xref:System.Windows.Controls.Calendar>. В частности <xref:System.Windows.Controls.DatePicker.IsTodayHighlighted%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.FirstDayOfWeek%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.BlackoutDates%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateStart%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateEnd%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDate%2A?displayProperty=nameWithType>, и <xref:System.Windows.Controls.DatePicker.SelectedDate%2A?displayProperty=nameWithType> свойства работать идентично их <xref:System.Windows.Controls.Calendar> аналоги. Для получения дополнительной информации см. <xref:System.Windows.Controls.Calendar>.  
  
 Пользователи могут ввести дату непосредственно в текстовое поле, которое задает <xref:System.Windows.Controls.DatePicker.Text%2A> свойства. Если <xref:System.Windows.Controls.DatePicker> не удается преобразовать введенную строку в допустимую дату <xref:System.Windows.Controls.DatePicker.DateValidationError> возникает событие. По умолчанию это приводит к возникновению исключения, но обработчик событий для <xref:System.Windows.Controls.DatePicker.DateValidationError> можно задать <xref:System.Windows.Controls.DatePickerDateValidationErrorEventArgs.ThrowException%2A> свойства `false` и предотвратить возникновение исключения.  
  
## <a name="see-also"></a>См. также  
 [Элементы управления](../../../../docs/framework/wpf/controls/index.md)  
 [Стилизация и использование шаблонов](../../../../docs/framework/wpf/controls/styling-and-templating.md)

---
title: "Практическое руководство. Выполнение операции перетаскивания между приложениями"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: drag and drop [Windows Forms], between applications
ms.assetid: fa347436-2b12-4dd6-8507-59d7241f6a06
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 513c6b2a15502625e4b42aeee4947ff36e4bfd17
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-perform-drag-and-drop-operations-between-applications"></a>Практическое руководство. Выполнение операции перетаскивания между приложениями
Выполнение операций перетаскивания между приложениями не отличается от реализации этой операции внутри приложения до тех пор, пока поведение участвующих приложений соответствует "контракту" между свойствами <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A> и <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.  
  
 В следующей процедуре будет использоваться созданное вами приложение Windows и текстовый редактора WordPad, который входит в состав операционной системы Windows, для выполнения операций перетаскивания между приложениями. WordPad имеет определенный набор допустимых действий для перетаскивания текста; приложение Windows, для которого будет написан код, будет использовать эти действия для успешного завершения операции перетаскивания.  
  
### <a name="to-perform-a-drag-and-drop-procedure-between-applications"></a>Выполнение операции перетаскивания между приложениями  
  
1.  Создайте новое приложение Windows Forms.  
  
2.  Добавьте элемент управления <xref:System.Windows.Forms.TextBox> в форму.  
  
3.  Настройте элемент управления <xref:System.Windows.Forms.TextBox> для получения перетаскиваемых данных.  
  
     Дополнительные сведения см. в разделе [Пошаговое руководство: выполнение операции перетаскивания и вставки в Windows Forms](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).  
  
4.  Запустите приложение Windows и во время выполнения приложения запустите WordPad.  
  
     WordPad — это текстовый редактор, установленный операционной системой Windows, который позволяет выполнять операции перетаскивания. Он доступен, нажав клавишу **запустить** кнопку выбора **запуска**и введя `WordPad` в текстовом поле **запуска** диалоговое окно и щелкнув **ОК**.  
  
5.  После открытия WordPad введите в нем строку текста.  
  
6.  Используя мышь, выделите текст и перетащите выделенный текст на элемент управления <xref:System.Windows.Forms.TextBox> в приложение Windows.  
  
     Обратите внимание, что, когда указатель мыши находится над элементом управления <xref:System.Windows.Forms.TextBox>, (и, следовательно, инициируется событие <xref:System.Windows.Forms.Control.DragEnter>), курсор изменяется и можно отпустить выделенный текст на элемент управления <xref:System.Windows.Forms.TextBox>.  
  
     Кроме того, можно настроить элемент управления <xref:System.Windows.Forms.TextBox> так, чтобы можно было перетаскивать текстовые строки в WordPad. Дополнительные сведения см. в разделе [Пошаговое руководство: выполнение операции перетаскивания и вставки в Windows Forms](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Добавление данных в буфер обмена](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)  
 [Практическое руководство. Извлечение данных из буфера обмена](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)  
 [Операции перетаскивания и поддержка буфера обмена](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)

---
title: "Практическое руководство. Создание пользовательского элемента Panel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF]
- custom Panel elements [WPF]
ms.assetid: e0df4f1e-8c07-4e86-89a3-e22acfffdc2a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7e7cca5b6f7a0d5085e70c4ab6ac33ff83b75217
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-custom-panel-element"></a>Практическое руководство. Создание пользовательского элемента Panel
## <a name="example"></a>Пример  
 В этом примере показан способ переопределения поведения по умолчанию <xref:System.Windows.Controls.Panel> элемент и создание пользовательских элементов макета, производных от <xref:System.Windows.Controls.Panel>.  
  
 В примере определяется простой пользовательский <xref:System.Windows.Controls.Panel> элемент с именем `PlotPanel`, который размещает дочерние элементы в соответствии с двумя жестко координаты x и y-. В этом примере `x` и `y` устанавливаются равными `50`; таким образом, все дочерние элементы располагаются в этом расположении на x и y осей.  
  
 Чтобы реализовать пользовательскую <xref:System.Windows.Controls.Panel> поведения, в примере используется <xref:System.Windows.FrameworkElement.MeasureOverride%2A> и <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> методы. Каждый метод возвращает <xref:System.Windows.Size> данные, необходимые для размещения и отображения дочерних элементов.  
  
 [!code-cpp[PlotPanel#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## <a name="see-also"></a>См. также  
 <xref:System.Windows.Controls.Panel>  
 [Общие сведения о панелях](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Создать пользовательский образец панели с переносом содержимого](http://go.microsoft.com/fwlink/?LinkID=159979)

---
title: "Whitespace Processing in XAML | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "East Asian characters [XAML Services]"
  - "XAML [XAML Services], whitespace processing"
  - "whitespace processing in XAML [XAML Services]"
  - "characters [XAML Services], East Asian"
ms.assetid: cc9cc377-7544-4fd0-b65b-117b90bb0b23
caps.latest.revision: 20
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 19
---
# Whitespace Processing in XAML
Согласно правилам языка XAML значащие пробелы должны обрабатываться реализации процессора [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]. В этом разделе описываются эти правила языка XAML. Здесь также описывается обработка дополнительных пробелов, которая определяется в реализации [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] процессора XAML и модуле записи XAML для сериализации.  
  
<a name="whitespace_definition"></a>   
## Определение пробела  
 В соответствии с [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)] символы пробелов в [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] — это пробел, перевод строки и табуляция. Это значения [!INCLUDE[TLA#tla_unicode](../../../includes/tlasharptla-unicode-md.md)] 0020, 000A и 0009 соответственно.  
  
<a name="whitespace_normalization"></a>   
## Нормализация пробелов  
 По умолчанию выполняется следующая нормализации пробелов, когда процессор [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] обрабатывает файл [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)].  
  
1.  Символы перевода строки между восточно\-азиатскими символами удаляются. Определение этого термина см. в разделе "Символы восточно\-азиатских языков" далее.  
  
2.  Все символы пробелов \(пробел, перевод строки, табуляция\) преобразуются в пробелы.  
  
3.  Все последовательные пробелы удаляются и заменяется одним пробелом.  
  
4.  Пробел после открывающего тега удаляется.  
  
5.  Пробел перед закрывающим тегом удаляется.  
  
 "Default" соответствует состоянию, обозначаемому значением атрибута [XML: space](../../../docs/framework/xaml-services/xml-space-handling-in-xaml.md) по умолчанию.  
  
<a name="whitespace_in_inner_text_and_string_primitives"></a>   
## Пробел во внутреннем тексте и строковые примитивы  
 Приведенные выше правила нормализации применяются к тексту внутри элементов XAML. После нормализации обработчик XAML преобразует любой внутренний текст в соответствующий тип следующим образом.  
  
-   Если тип свойства не является коллекцией и типом <xref:System.Object>, обработчик XAML попытается преобразовать его в этот тип, используя преобразователь типов. Неудачное преобразование приводит к ошибке во время компиляции.  
  
-   Если тип свойства — это коллекция, а внутренний текст не прерывается \(не содержит промежуточных тегов элементов\), внутренний текст анализируется как один <xref:System.String>. Если тип коллекции не может принять <xref:System.String>, это также приводит к ошибке во время компиляции.  
  
-   Если тип свойства — <xref:System.Object>, внутренний текст анализируется как один <xref:System.String>. Если существуют промежуточные теги элементов, это приводит к ошибке во время компиляции, поскольку <xref:System.Object> подразумевает один объект \(<xref:System.String> или другой\).  
  
-   Если тип свойства — коллекция, а внутренний текст прерывается, первая подстрока преобразуется в <xref:System.String> и добавляется как элемент коллекции, затем промежуточный элемент добавляется как элемент коллекции, и, наконец, конечная подстрока \(если таковая имеется\) добавляется в коллекцию как третий элемент <xref:System.String>.  
  
<a name="preserving_whitespace"></a>   
## Сохранение пробелов  
 Существует несколько методов для сохранения пробелов в исходном [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)], чтобы не затрагивать окончательное представление при нормализации пробелов обработчиком [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)].  
  
 **xml:space\="preserve"**: укажите этот атрибут на уровне элемента, где требуется сохранение пробелов. При этом сохраняются все пробелы, включая те, что могут быть добавлены приложениями редактирования кода для выравнивания элементов и улучшения визуального восприятия. Однако то, отображаются ли эти пробелы, определяется моделью контента элемента. Не рекомендуется указывать `xml:space="preserve"` на корневом уровне, так как большинство объектных моделей не рассматривает пробелы как значащие вне зависимости от способа установки атрибута. Глобальная установка `xml:space` может отрицательно повлиять на производительность обработки XAML \(в частности, на сериализацию\) в некоторых реализациях. Рекомендуется задавать атрибут только на уровне элементов, отображающих пробелы в пределах строки или представляющих коллекции значащих пробелов.  
  
 **Сущности и неразрывные пробелы**: [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] поддерживает размещение любой сущности [!INCLUDE[TLA#tla_unicode](../../../includes/tlasharptla-unicode-md.md)] в модели объектов текста. Вы можете использовать выделенные сущности, такие как неразрывный пробел \(&\#160; в кодировке UTF\-8\). Можно также использовать элементы управления форматированным текстом, поддерживающие неразрывные пробелы. Следует соблюдать осторожность при использовании сущностей для имитации характеристики разметки, таких как отступы, поскольку выходные данные сущностей во время выполнения зависят от множества факторов, при этом возможности формирования получения отступов в типичной системе разметки, например правильное использование панелей и полей, ограничены. Например, сущности сопоставляются со шрифтами и могут изменять размер после выбора шрифта пользователем.  
  
<a name="east_asian_characters"></a>   
## Символы восточно\-азиатских языков  
 "Символы восточно\-азиатских языков" определяется как набор символов [!INCLUDE[TLA2#tla_unicode](../../../includes/tla2sharptla-unicode-md.md)] в диапазоне от U\+20000 до U\+2FFFD и от U\+30000 до U\+3FFFD. Это подмножество также иногда называют "CJK\-иероглифами". Дополнительные сведения см. на веб\-сайте [http:\/\/www.unicode.org](http://www.unicode.org/).  
  
<a name="whitespace_and_text_content_models"></a>   
## Пробелы и модели текстового содержимого  
 На практике сохранение пробелов необходимо только для подмножества всевозможных моделей содержимого. Это подмножество состоит из моделей содержимого, которые могут принимать одноэлементный тип <xref:System.String> в определенной форме, выделенную коллекцию <xref:System.String> или сочетание <xref:System.String> и других типов в коллекции <xref:System.Collections.IList> или <xref:System.Collections.Generic.ICollection%601>.  
  
### Пробелы и модели текстового содержимого в WPF  
 Для наглядности оставшаяся часть этого подраздела ссылается на конкретные типы, определенные в WPF. Функции обработки пробелов, описанные в этом разделе, обычно относятся к службами XAML .NET Framework и WPF. Чтобы увидеть это в действии, можно поэкспериментировать с некоторой разметкой WPF XAML, просмотреть результаты в графе объектов и снова сериализовать их в разметку.  
  
 Даже для моделей содержимого, которые могут принимать строки, поведение по умолчанию заключается в том, что любой оставшийся пробел не рассматривается как значащий. Например, <xref:System.Windows.Controls.ListBox> принимает <xref:System.Collections.IList>, однако символы пробелов \(такие как символ перевода строки между каждым <xref:System.Windows.Controls.ListBoxItem>\) не сохраняются и не отображаются. Попытка использовать символ перевода строки в качестве разделителей между строками для элементов <xref:System.Windows.Controls.ListBoxItem> вообще не даст результатов. Строки, разделенные символами перевода строки, считаются одной строкой и одним элементом.  
  
 Коллекции, которые обрабатывают пробелы как значащие, обычно являются частью модели потокового документа . Основная коллекция, поддерживающая сохранение пробелов — это <xref:System.Windows.Documents.InlineCollection>. Этот класс коллекции объявлен с <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>. При обнаружении этого атрибута процессор [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] обрабатывает пробелы в коллекции как значащие. Сочетание `xml:space="preserve"` и пробелов в коллекции <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> означает, что все пробелы сохраняются и отображаются. Сочетание `xml:space="default"` и пробелов в <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> приводит к начальной нормализации пробелов, как описано выше, при которой сохраняется один пробел в определенных позициях, после чего эти пробелы будут сохранены и показаны. Предпочтительное для вас поведение выбираете вы. Следует выборочно использовать `xml:space`, чтобы включить желаемое поведение.  
  
 Кроме того, некоторые встроенные элементы, имеющие отношение к разрыву строки в модели потокового документа, намеренно не должны отображать лишние пробелы даже в коллекции значащих пробелов. Например, элемент <xref:System.Windows.Documents.LineBreak> используется для той же цели, что и тег \<BR\/\> в [!INCLUDE[TLA2#tla_html](../../../includes/tla2sharptla-html-md.md)], а для удобства чтения в разметке <xref:System.Windows.Documents.LineBreak> обычно отделяется от любого последующего текста автоматически добавленным символом перевода строки. Этот символ не следует нормализовать, чтобы он не стал начальным пробелом в следующей строке. Чтобы включить это поведение, в определении класса для элемента <xref:System.Windows.Documents.LineBreak> применяется <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>, который затем интерпретируется процессором [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] так, чтобы пробелы вокруг <xref:System.Windows.Documents.LineBreak> всегда отсекались.  
  
## См. также  
 [Обзор XAML \(WPF\)](../../../ocs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [XML Character Entities and XAML](../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md)   
 [xml:space Handling in XAML](../../../docs/framework/xaml-services/xml-space-handling-in-xaml.md)
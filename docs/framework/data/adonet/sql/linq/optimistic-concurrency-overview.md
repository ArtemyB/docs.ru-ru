---
title: "Общие сведения об оптимистической блокировке"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2e38512-d0c8-4807-b30a-cb7e30338694
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 52e83f443c0ae74587b4585beb51ddbeb093486a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="optimistic-concurrency-overview"></a>Общие сведения об оптимистической блокировке
Технология [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] поддерживает средства управления оптимистическим параллелизмом. В следующей таблице описаны термины, применяемые к оптимистическому параллелизму в [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] документации:  
  
|Термины|Описание|  
|-----------|-----------------|  
|параллельность|Ситуация, при которой несколько пользователей одновременно пытаются обновить одну строку базы данных.|  
|конфликт параллелизма|Ситуация, при которой несколько пользователей одновременно пытаются отправить конфликтующие значения в один или несколько столбцов строки.|  
|управление параллелизмом|Метод, используемый для разрешения конфликтов параллелизма.|  
|оптимистический контроль параллелизма|Метод, при котором, прежде чем разрешить отправку изменений, определяется, не были ли изменены значения в строке другими транзакциями.<br /><br /> Этот метод противоположен *управление пессимистичным параллелизмом*, котором запись блокируется для предотвращения конфликтов параллелизма.<br /><br /> *Оптимистический* управления называется потому, что вероятность конфликта с другим работать маловероятно, что одна транзакция здесь.|  
|разрешение конфликтов|Процесс обновления конфликтующего элемента путем повторного запроса к базе данных и последующего согласования различий.<br /><br /> При обновлении объекта средство отслеживания изменений [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] содержит следующие данные:<br /><br /> -Проверьте значения первоначально берутся из базы данных и используется для обновления.<br />-Новые базы данных значения из последующего запроса.<br /><br /> После этого [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] определяет, является ли объект конфликтующим (то есть изменилось ли одно или несколько значений его членов). Если объект является конфликтующим, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] далее определяет, какие его члены конфликтуют.<br /><br /> Каждый конфликт члена, обнаруженный [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], добавляется в список конфликтов.|  
  
 В [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] объектной модели *оптимистический конфликт параллелизма* возникает, если выполняются оба из следующих условий:  
  
-   Клиент пытается отправить изменения в базу данных.  
  
-   Одно или несколько значений проверки обновлений было обновлено в базе данных с момента последнего чтения этих значений клиентом.  
  
 Процесс разрешения этого конфликта включает обнаружение конфликтующих членов и принятие решения о том, какие действия следует к ним применить.  
  
> [!NOTE]
>  В проверках оптимистического параллелизма участвуют только те члены, которые сопоставлены свойству <xref:System.Data.Linq.Mapping.UpdateCheck.Always> или <xref:System.Data.Linq.Mapping.UpdateCheck.WhenChanged>. Для членов, сопоставленных свойству <xref:System.Data.Linq.Mapping.UpdateCheck.Never>, никаких проверок не производится. Для получения дополнительной информации см. <xref:System.Data.Linq.Mapping.UpdateCheck>.  
  
## <a name="example"></a>Пример  
 Рассмотрим в качестве примера следующий сценарий, в котором Пользователь1 начинает подготовку к обновлению, запрашивая строку в базе данных. Пользователь1 получает строку со значениями "Алексеи", "Мария" и "Продажи".  
  
 Пользователь1 хочет изменить значение в столбце "Менеджер" на "Алексей", а значение в столбце "Отдел" на "Маркетинг". Прежде чем Пользователь1 смог отправить эти изменения, Пользователь2 отправил изменения в эту базу данных. Поэтому теперь значение в столбце "Помощник" изменилось на "Инна", а значение в столбце "Отдел" изменилось на "Обслуживание".  
  
 Когда пользователь Пользователь1 пытается отправить изменения, происходит сбой при отправке и возникает исключение <xref:System.Data.Linq.ChangeConflictException>. Этот результат происходит по той причине, что значения базы данных для столбцов "Помощник" и "Отдел" не совпадают с ожидаемыми значениями. Члены, представляющие столбцы "Помощник" и "Отдел", являются конфликтующими. Эта ситуация обобщается в следующей таблице.  
  
||Диспетчер|Помощник|Отдел|  
|------|-------------|---------------|----------------|  
|Исходное состояние|Алексеи|Мария|Продажи|  
|Пользователь1|Алексей||Маркетинг|  
|Пользователь2||Инна|Служба|  
  
 Подобные конфликты можно разрешать различными способами. Дополнительные сведения см. в разделе [как: управление конфликтами изменений](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).  
  
## <a name="conflict-detection-and-resolution-checklist"></a>Контрольный список обнаружения и разрешения конфликтов  
 Конфликты можно обнаруживать и разрешать на любом уровне детализации. С одной стороны, можно разрешить все конфликты одним из трех способов (см. <xref:System.Data.Linq.RefreshMode>) без каких-либо дополнительных действий. С другой стороны, можно указать конкретное действие для каждого типа конфликта и для каждого конфликтующего члена.  
  
-   Укажите или проверьте параметры <xref:System.Data.Linq.Mapping.UpdateCheck> в объектной модели.  
  
     Дополнительные сведения см. в разделе [как: укажите каких элементов проверяются на наличие конфликтов параллелизма](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md).  
  
-   В блоке "try/catch" вызова метода <xref:System.Data.Linq.DataContext.SubmitChanges%2A> укажите, в какой точке должны вызываться исключения.  
  
     Дополнительные сведения см. в разделе [как: указать, когда возникают исключения параллелизма](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md).  
  
-   Определите уровень детализации извлекаемых сведений о конфликте и вставьте соответствующий код в блок "try/catch".  
  
     Дополнительные сведения см. в разделе [как: получение сведений о конфликте сущностей](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-entity-conflict-information.md) и [как: получение сведений о конфликте членов](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-member-conflict-information.md).  
  
-   Включить в вашей `try` / `catch` кода способ разрешения различных обнаруженных конфликтов.  
  
     Дополнительные сведения см. в разделе [как: разрешение конфликтов с сохранением значений базы данных](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md), [как: разрешение конфликтов путем перезаписи значений базы данных](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md), и [как: разрешение конфликтов, объединение значениями из базы данных](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-merging-with-database-values.md).  
  
## <a name="linq-to-sql-types-that-support-conflict-discovery-and-resolution"></a>Типы LINQ to SQL, поддерживающие обнаружение и разрешение конфликтов  
 Ниже перечислены классы и функции, поддерживающие разрешение конфликтов при оптимистическом параллелизме в [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
-   <xref:System.Data.Linq.ObjectChangeConflict?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.MemberChangeConflict?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.ChangeConflictCollection?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.ChangeConflictException?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.DataContext.ChangeConflicts%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.DataContext.Refresh%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.Mapping.UpdateCheck?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.RefreshMode?displayProperty=nameWithType>  
  
## <a name="see-also"></a>См. также  
 [Как: управление конфликтами изменений](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)

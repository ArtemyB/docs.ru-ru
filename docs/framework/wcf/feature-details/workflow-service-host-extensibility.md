---
title: "Расширяемость узла службы рабочих процессов | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c0e8f7bb-cb13-49ec-852f-b85d7c23972f
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# Расширяемость узла службы рабочих процессов
Платформа [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] содержит класс <xref:System.ServiceModel.Activities.WorkflowServiceHost> для размещения служб рабочих процессов.  Этот класс используется при размещении служб рабочих процессов в управляемом приложении или службе Windows.  Этот класс также используется при размещении службы рабочего процесса в службах IIS или службе активации Windows \(WAS\).  Класс <xref:System.ServiceModel.Activities.WorkflowServiceHost> обеспечивает точки расширения, которые дают возможность добавлять пользовательские расширения, изменять неактивное поведение и размещать рабочие процессы, не относящиеся к службе \(то есть те, которые не используют обмен сообщениями\).  
  
## Расширения размещения службы рабочего процесса  
 Класс <xref:System.ServiceModel.Activities.WorkflowServiceHost> содержит свойство <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> типа <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager>, методы которого позволяют добавлять расширения к <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  Метод <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager.Add%2A> используется для добавления расширения в каждый из экземпляров.  Указанный делегат вызывается для создания нового расширения при создании экземпляра службы рабочего процесса или его загрузке из хранилища сохраняемости.  Метод <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager.Add%2A> используется для добавления расширения для каждого узла службы рабочего процесса, один экземпляр расширения совместно используется всеми экземплярами службы рабочего процесса.  
  
## Реакция на необработанные исключения  
 Поведение <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> позволяет задать действие, которое должно быть выполнено в случае, если в службе рабочего процесса появляется необработанное исключение.  Свойство <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior.Action%2A> определяет одно из следующих значений <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction>.  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction> \- аварийно завершает работу экземпляра службы рабочего процесса.  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction> \- выполняет откат до последнего сохраненного состояния и приостанавливает экземпляр службы рабочего процесса.  Это происходит только в случае, если рабочий процесс уже хотя бы раз был сохранен.  В противном случае экземпляр рабочего процесса аварийно завершается.  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction> \- отменяет экземпляр.  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction> \- завершает работу экземпляра.  
  
 Это поведение может быть настроено в коде, как показано в следующем примере.  
  
```csharp  
host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.Abandon });  
  
```  
  
 Кроме того, его можно настроить в файле конфигурации, как показано в следующем примере.  
  
```vb-c#  
<behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <workflowUnhandledExceptionBehavior action="Abandon" />        
        </behavior>  
      </serviceBehaviors>  
  
```  
  
## Размещение рабочих процессов, не относящихся к службе  
 Объект <xref:System.ServiceModel.Activities.WorkflowServiceHost> может быть использован для размещения рабочих процессов, не относящихся к службе, а также рабочих процессов, которые либо не начинают работу с действия <xref:System.ServiceModel.Activities.Receive>, либо не используют обмен сообщениями.  Службы рабочих процессов, как правило, начинают работу с действия <xref:System.ServiceModel.Activities.Receive>.  Когда <xref:System.ServiceModel.Activities.WorkflowServiceHost> получает сообщение для службы рабочего процесса, создается новый экземпляр службы рабочего процесса \(если он не работает и не сохранен\).  Если рабочий процесс не начал работу с действия Receive, он не не может быть запущен отправкой сообщения, поскольку отсутствует действие, которое может принять это сообщение.  Чтобы разместить рабочий процесс, не являющийся службой, создайте класс, наследующий <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, и переопределите в нем методы <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A>, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A> и <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnResolveBookmark%2A>.  Переопределите метод <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A>, если необходимо задать определенный идентификатор экземпляра.  Переопределите метод <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A> для создания контекста создания рабочего процесса или заполните экземпляр из существующего <xref:System.ServiceModel.Activities.WorkflowCreationContext>.  Переопределите метод <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnResolveBookmark%2A>, если необходимо вручную извлекать закладку из входящего сообщения.  При переопределении этого метода в его тексте необходимо вызвать метод <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A>, чтобы ответить на сообщение, отправленное конечной точкой WorkflowHostingEndpoint.  Если этого не сделать, предел <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> может быть превышен.  В двусторонних контрактах пользователь может столкнуться с ошибкой при вызове метода <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A>, связанной с тем, что клиент не получил ответ.  В односторонних контрактах может возникнуть ситуация, когда ошибка, связанная с тем, что метод <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> не вызван, будет обнаружена только после превышения предела <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, когда уже слишком поздно.  Дополнительные сведения см. в разделе [Закладка возобновления для конечной точки WorkflowHostingEndpoint](../../../../docs/framework/windows-workflow-foundation/samples/workflowhostingendpoint-resume-bookmark.md)Чтобы создать новый экземпляр рабочего процесса, не относящегося к службе, необходимо объявить контракт службы, в котором определена операция создания нового экземпляра.  Эта операция должна принимать аргумент IDictionary \<string, object\>, содержащий все необходимые параметры рабочего процесса.  Этот контракт неявным образом реализуется классом, производным от <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>.  При размещении рабочего процесса добавьте к узлу экземпляр класса, производного от <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, вызвав метод <xref:System.ServiceModel.Activities.WorkflowServiceHost.AddServiceEndpoint%2A>, а затем вызовите метод <xref:System.ServiceModel.Activities.WorkflowServiceHost.Open%2A>.  Чтобы создать экземпляр рабочего процесса, создайте фабрику <xref:System.ServiceModel.ChannelFactory%601> для типа контракта службы и вызовите метод <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A>.  Затем можно вызвать операцию создания, определенную в контракте службы.  
  
## См. также  
 [Службы рабочего процесса](../../../../docs/framework/wcf/feature-details/workflow-services.md)   
 [Действия обмена сообщениями](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
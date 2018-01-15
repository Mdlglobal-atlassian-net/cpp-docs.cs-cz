---
title: "Iumsunblocknotification – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IUMSUnblockNotification
- CONCRTRM/concurrency::IUMSUnblockNotification
- CONCRTRM/concurrency::IUMSUnblockNotification::IUMSUnblockNotification::GetContext
- CONCRTRM/concurrency::IUMSUnblockNotification::IUMSUnblockNotification::GetNextUnblockNotification
dev_langs: C++
helpviewer_keywords: IUMSUnblockNotification structure
ms.assetid: eaca9529-c1cc-472b-8ec6-722a1ff0fa2a
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3febe10f7c71e1c1d478dd6f6b6f565c4134e033
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="iumsunblocknotification-structure"></a>IUMSUnblockNotification – struktura
Představuje oznámení ze Správce prostředků, proxy přístup z více vláken, která blokovaný a aktivaci vraťte se do plánovače určené plánování kontextu má odblokováno a je připravený k naplánování. Toto rozhraní je neplatný, jakmile kontext přidružený spuštění proxy přístup z více vláken, vrátí z `GetContext` je přeplánovat metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct IUMSUnblockNotification;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Iumsunblocknotification::getcontext –](#getcontext)|Vrátí `IExecutionContext` rozhraní pro kontext provádění přidružená k proxy serveru, který má odblokováno přístup z více vláken. Po návratu tato metoda a základní kontext provádění byl znovu naplánován prostřednictvím volání `IThreadProxy::SwitchTo` metoda, toto rozhraní je již neplatný.|  
|[Iumsunblocknotification::getnextunblocknotification –](#getnextunblocknotification)|Vrací další `IUMSUnblockNotification` rozhraní v řetězu vrátila z metody `IUMSCompletionList::GetUnblockNotifications`.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IUMSUnblockNotification`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrtrm.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="getcontext"></a>Iumsunblocknotification::getcontext – metoda  
 Vrátí `IExecutionContext` rozhraní pro kontext provádění přidružená k proxy serveru, který má odblokováno přístup z více vláken. Po návratu tato metoda a základní kontext provádění byl znovu naplánován prostřednictvím volání `IThreadProxy::SwitchTo` metoda, toto rozhraní je již neplatný.  
  
```
virtual IExecutionContext* GetContext() = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `IExecutionContext` Rozhraní pro provádění kontext, který má přístup z více vláken proxy serveru, který má odblokováno.  
  
##  <a name="getnextunblocknotification"></a>Iumsunblocknotification::getnextunblocknotification – metoda  
 Vrací další `IUMSUnblockNotification` rozhraní v řetězu vrátila z metody `IUMSCompletionList::GetUnblockNotifications`.  
  
```
virtual IUMSUnblockNotification* GetNextUnblockNotification() = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Další `IUMSUnblockNotification` rozhraní v řetězu vrátila z metody `IUMSCompletionList::GetUnblockNotifications`.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [Struktura rozhraní IUMSScheduler](iumsscheduler-structure.md)   
 [IUMSCompletionList – struktura](iumscompletionlist-structure.md)

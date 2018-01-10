---
title: "Iumscompletionlist – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IUMSCompletionList
- CONCRTRM/concurrency::IUMSCompletionList
- CONCRTRM/concurrency::IUMSCompletionList::IUMSCompletionList::GetUnblockNotifications
dev_langs: C++
helpviewer_keywords: IUMSCompletionList structure
ms.assetid: 81b5250e-3065-492c-b20d-2cdabf12271a
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 50fd2381174e947e243ad6aa40516be5fd728902
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="iumscompletionlist-structure"></a>IUMSCompletionList – struktura
Představuje seznam dokončení UMS. Při plánování vláken UMS bloky plánovače určené kontextu je odeslat, aby rozhodnutí o při plánování v kořenovém adresáři základní virtuálních procesorů, zatímco původní vlákno je blokované. Při původní vlákno odblokuje, fronty je operační systém do seznamu dokončení, která je přístupná prostřednictvím tohoto rozhraní. Plánovač můžete dotazovat seznamu dokončení v určené plánování kontext nebo jiné místo, které vyhledávání pro práci.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct IUMSCompletionList;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Iumscompletionlist::getunblocknotifications –](#getunblocknotifications)|Načte řetězec `IUMSUnblockNotification` rozhraní představující provádění kontexty, jejichž přidružené vlákno proxy mít odblokováno od posledního tato metoda byla vyvolána.|  
  
## <a name="remarks"></a>Poznámky  
 Plánovače musí být neobvykle pozor, o jaké akce se provádí po použití tohoto rozhraní dequeue – položek v seznamu dokončení. Položky musí být umístěny na plánovače seznam spustitelného kontexty a co nejdříve se obecně dostupné. Je zcela možné, že dequeued položky nebyla zadána vlastnictví libovolný zámku. Plánovač můžete provést žádné volání libovolné funkce, která může blokovat mezi volání dequeue položky a umístění tyto položky na seznamu, který může být obecně dostupný v plánovače.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IUMSCompletionList`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrtrm.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="getunblocknotifications"></a>Iumscompletionlist::getunblocknotifications – metoda  
 Načte řetězec `IUMSUnblockNotification` rozhraní představující provádění kontexty, jejichž přidružené vlákno proxy mít odblokováno od posledního tato metoda byla vyvolána.  
  
```
virtual IUMSUnblockNotification *GetUnblockNotifications() = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Řetězec `IUMSUnblockNotification` rozhraní.  
  
### <a name="remarks"></a>Poznámky  
 Vrácená oznámení jsou neplatné, jakmile jsou přeplánovat kontexty provádění.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [Struktura rozhraní IUMSScheduler](iumsscheduler-structure.md)   
 [IUMSUnblockNotification – struktura](iumsunblocknotification-structure.md)

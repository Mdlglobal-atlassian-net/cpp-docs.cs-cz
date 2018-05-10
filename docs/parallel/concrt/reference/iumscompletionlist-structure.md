---
title: Iumscompletionlist – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- IUMSCompletionList
- CONCRTRM/concurrency::IUMSCompletionList
- CONCRTRM/concurrency::IUMSCompletionList::IUMSCompletionList::GetUnblockNotifications
dev_langs:
- C++
helpviewer_keywords:
- IUMSCompletionList structure
ms.assetid: 81b5250e-3065-492c-b20d-2cdabf12271a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6ee957355510a2f62f5317d330403dc246ee8f2e
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
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
  
##  <a name="getunblocknotifications"></a>  Iumscompletionlist::getunblocknotifications – metoda  
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

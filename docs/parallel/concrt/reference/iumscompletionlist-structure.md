---
title: IUMSCompletionList – struktura
ms.date: 11/04/2016
f1_keywords:
- IUMSCompletionList
- CONCRTRM/concurrency::IUMSCompletionList
- CONCRTRM/concurrency::IUMSCompletionList::IUMSCompletionList::GetUnblockNotifications
helpviewer_keywords:
- IUMSCompletionList structure
ms.assetid: 81b5250e-3065-492c-b20d-2cdabf12271a
ms.openlocfilehash: c388cc98aedbd35b2d0e00a4653a85a47abcb838
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368123"
---
# <a name="iumscompletionlist-structure"></a>IUMSCompletionList – struktura

Představuje seznam dokončení ums. Když vlákno Služby UMS blokuje, je odeslán kontext určeného plánování plánovače, aby bylo možné rozhodnout, co naplánovat na kořen základnívirtuální procesor, zatímco původní vlákno je blokováno. Když se původní vlákno odblokuje, operační systém jej zařadí do fronty do seznamu dokončení, který je přístupný prostřednictvím tohoto rozhraní. Plánovač může dotazovat seznam dokončení na určeném kontextu plánování nebo na jakémkoli jiném místě, kde hledá práci.

## <a name="syntax"></a>Syntaxe

```cpp
struct IUMSCompletionList;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[IUMSCompletionList::GetUnblockNotifications](#getunblocknotifications)|Načte řetězec `IUMSUnblockNotification` rozhraní představující kontexty spuštění, jejichž přidružené proxy vlákna odblokovány od posledního použití této metody.|

## <a name="remarks"></a>Poznámky

Plánovač musí být mimořádně opatrní, jaké akce jsou prováděny po využití tohoto rozhraní k vyřazení položek ze seznamu dokončení. Položky by měly být umístěny na seznamu plánovače spustitelné kontexty a obecně přístupné co nejdříve. Je zcela možné, že jedna z položek dequeued byla udělena vlastnictví libovolného zámku. Plánovač může provádět žádná volání libovolné funkce, která může blokovat mezi volání dequeue položky a umístění těchto položek v seznamu, který lze obecně přistupovat z v rámci plánovače.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IUMSCompletionList`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm.h

**Obor názvů:** souběžnost

## <a name="iumscompletionlistgetunblocknotifications-method"></a><a name="getunblocknotifications"></a>IUMSCompletionList::Metoda GetUnblockNotifications

Načte řetězec `IUMSUnblockNotification` rozhraní představující kontexty spuštění, jejichž přidružené proxy vlákna odblokovány od posledního použití této metody.

```cpp
virtual IUMSUnblockNotification *GetUnblockNotifications() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Řetězec `IUMSUnblockNotification` rozhraní.

### <a name="remarks"></a>Poznámky

Vrácená oznámení jsou neplatná, jakmile jsou kontexty spuštění přeplánovány.

## <a name="see-also"></a>Viz také

[obor názvů souběžnosti](concurrency-namespace.md)<br/>
[IUMSScheduler – struktura](iumsscheduler-structure.md)<br/>
[IUMSUnblockNotification – struktura](iumsunblocknotification-structure.md)

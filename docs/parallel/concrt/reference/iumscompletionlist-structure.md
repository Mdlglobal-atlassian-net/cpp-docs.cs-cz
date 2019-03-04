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
ms.openlocfilehash: 567b8668934d81c49757660d1a60ca74eb033e68
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57273907"
---
# <a name="iumscompletionlist-structure"></a>IUMSCompletionList – struktura

Představuje seznam pro doplňování UMS. Při plánování určené plánovače vlákno blokováno UMS kontext je odeslána k provedení rozhodnutí toho, jak naplánovat na základního kořenového virtuálního procesoru, zatímco původní vlákno blokované. Když se původní vlákno odblokuje, operační systém zařadí do fronty se do seznamu dokončení, která je dostupná prostřednictvím tohoto rozhraní. Plánovač můžete dotazovat v seznamu dokončení na určené plánování kontextu nebo druhém místě, které prohledává pro práci.

## <a name="syntax"></a>Syntaxe

```
struct IUMSCompletionList;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Iumscompletionlist::getunblocknotifications –](#getunblocknotifications)|Načte řetězec `IUMSUnblockNotification` rozhraní představující kontexty provádění, jejíž přidružené vlákno proxy servery mají odblokováno od posledního tato metoda byla vyvolána.|

## <a name="remarks"></a>Poznámky

Plánovač musí být neobyčejně pozor, o jaké akce se provádí po použití tohoto rozhraní k vyřazení položek v seznamu dokončení. Položky musí být umístěny na plánovače seznam spustitelných kontextů a být obecně přístupné co nejdříve. Je zcela je to možné, že jednu z položek dequeued bylo přiděleno vlastnictví libovolného zámku. Plánovač můžete volat žádné libovolné funkce, které mohou blokovat mezi volání k vyřazení položek a umístění těchto položek na seznam, který je všeobecně přístupná z v rámci plánovače.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IUMSCompletionList`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm.h

**Namespace:** souběžnosti

##  <a name="getunblocknotifications"></a>  Iumscompletionlist::getunblocknotifications – metoda

Načte řetězec `IUMSUnblockNotification` rozhraní představující kontexty provádění, jejíž přidružené vlákno proxy servery mají odblokováno od posledního tato metoda byla vyvolána.

```
virtual IUMSUnblockNotification *GetUnblockNotifications() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Řetězec `IUMSUnblockNotification` rozhraní.

### <a name="remarks"></a>Poznámky

Vrácené oznámení jsou neplatné, jakmile se znovu naplánována kontexty provádění.

## <a name="see-also"></a>Viz také:

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[IUMSScheduler – struktura](iumsscheduler-structure.md)<br/>
[IUMSUnblockNotification – struktura](iumsunblocknotification-structure.md)

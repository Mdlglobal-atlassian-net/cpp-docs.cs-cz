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
ms.openlocfilehash: 02382ef4606a6e73804fcbd5ce7735ecf2f0dcc7
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140040"
---
# <a name="iumscompletionlist-structure"></a>IUMSCompletionList – struktura

Představuje seznam pro doplňování UMS. Když vlákno UMS blokuje, je určený plánovací kontext plánovače odeslán, aby bylo možné rozhodnout o tom, co naplánovat na podkladovém kořenu virtuálního procesoru v době, kdy je původní vlákno blokované. Když původní vlákno odblokuje, operační systém je zařadí do seznamu dokončení, který je přístupný prostřednictvím tohoto rozhraní. Plánovač může zadat dotaz na seznam pro doplňování v určeném kontextu plánování nebo na jakémkoli jiném místě, kde hledá práci.

## <a name="syntax"></a>Syntaxe

```cpp
struct IUMSCompletionList;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IUMSCompletionList –:: GetUnblockNotifications –](#getunblocknotifications)|Načítá řetěz `IUMSUnblockNotification` rozhraní reprezentující kontexty spuštění, jejichž proxy servery přidruženého vlákna byly odblokovány od posledního vyvolání této metody.|

## <a name="remarks"></a>Poznámky

Plánovač musí být neobyčejně pečlivě o tom, jaké akce se provádějí po použití tohoto rozhraní k vyřazení položek ze seznamu dokončení. Položky by se měly umístit do seznamu kontextů v Plánovači spustitelný a budou všeobecně dostupné, jakmile to bude možné. Je možné, že jedna z položek odstraněných z fronty dostala vlastnictví libovolného zámku. Scheduler nemůže bez jakýchkoli volání funkcí zablokovat volání vyřadit položky do fronty a umístění těchto položek v seznamu, ke kterému se dá všeobecně přistupovat v rámci plánovače.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IUMSCompletionList`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm. h

**Obor názvů:** souběžnost

## <a name="getunblocknotifications"></a>IUMSCompletionList –:: GetUnblockNotifications – – metoda

Načítá řetěz `IUMSUnblockNotification` rozhraní reprezentující kontexty spuštění, jejichž proxy servery přidruženého vlákna byly odblokovány od posledního vyvolání této metody.

```cpp
virtual IUMSUnblockNotification *GetUnblockNotifications() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Řetěz `IUMSUnblockNotification` rozhraní.

### <a name="remarks"></a>Poznámky

Po přeplánování kontextů spuštění jsou vrácená oznámení neplatná.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[IUMSScheduler – struktura](iumsscheduler-structure.md)<br/>
[IUMSUnblockNotification – struktura](iumsunblocknotification-structure.md)

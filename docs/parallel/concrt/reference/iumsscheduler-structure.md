---
title: Struktura rozhraní IUMSScheduler
ms.date: 11/04/2016
f1_keywords:
- IUMSScheduler
- CONCRTRM/concurrency::IUMSScheduler
- CONCRTRM/concurrency::IUMSScheduler::IUMSScheduler::SetCompletionList
helpviewer_keywords:
- IUMSScheduler structure
ms.assetid: 3a500225-4e02-4849-bb56-d744865f5870
ms.openlocfilehash: 0fd1ed90ca30c9c9e6815bb05b516f24b4f9a164
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50513786"
---
# <a name="iumsscheduler-structure"></a>Struktura rozhraní IUMSScheduler

Rozhraní pro abstrakci plánovače, která chce, aby správce prostředků modulu Runtime souběžnosti k předání zařízení uživatelského režimu plánovatelná vlákna (UMS). Resource Manager používá ke komunikaci s podprocesu plánovače UMS toto rozhraní. `IUMSScheduler` Rozhraní zdědí `IScheduler` rozhraní.

## <a name="syntax"></a>Syntaxe

```
struct IUMSScheduler : public IScheduler;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Iumsscheduler::setcompletionlist –](#setcompletionlist)|Přiřadí `IUMSCompletionList` rozhraní do fronty plánovače UMS vlákna.|

## <a name="remarks"></a>Poznámky

Pokud implementujete vlastní plánovač, který komunikuje s Resource Managerem a má být předán vaší plánovačem namísto běžné vlákna Win32 UMS vláken, by měla poskytnout implementaci položky `IUMSScheduler` rozhraní. Kromě toho byste měli nastavit hodnotu klíče zásad plánovače zásady `SchedulerKind` bude `UmsThreadDefault`. Pokud tato zásada určuje UMS vlákno `IScheduler` rozhraní, který je předán jako parametr, který se [iresourcemanager::registerscheduler –](iresourcemanager-structure.md#registerscheduler) metoda musí být `IUMSScheduler` rozhraní.

Správce prostředků se předá UMS vlákna pouze v operačních systémech, které mají funkci UMS. 64bitová verze operačních systémů s Windows 7 a vyšší verze podporují UMS vlákna. Pokud jste vytvořili zásadu plánovače s `SchedulerKind` klíč nastavený na hodnotu `UmsThreadDefault` a podkladová platforma nepodporuje UMS, hodnota `SchedulerKind` klíč na tuto zásadu se změní na hodnotu `ThreadScheduler`. Byste si měli vždy přečíst zpět tuto hodnotu zásady před očekává příjem UMS vlákna.

`IUMSScheduler` Rozhraní je jeden konec obousměrný kanál komunikace mezi plánovače a Resource Manageru. Druhém konci je reprezentována `IResourceManager` a `ISchedulerProxy` rozhraní, které jsou implementované pomocí Správce prostředků.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Ischeduler –](ischeduler-structure.md)

`IUMSScheduler`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm.h

**Namespace:** souběžnosti

##  <a name="setcompletionlist"></a>  Iumsscheduler::setcompletionlist – metoda

Přiřadí `IUMSCompletionList` rozhraní do fronty plánovače UMS vlákna.

```
virtual void SetCompletionList(_Inout_ IUMSCompletionList* pCompletionList) = 0;
```

### <a name="parameters"></a>Parametry

*pCompletionList*<br/>
Rozhraní seznamu dokončení pro Plánovač. Existuje jeden seznam za scheduler.

### <a name="remarks"></a>Poznámky

Správce prostředků se vyvolat tuto metodu na plánovače, která určuje, že chce UMS vlákna po Plánovač požádal o počáteční přidělení prostředků. Můžete použít Plánovač `IUMSCompletionList` rozhraní k určení, kdy mají odblokováno UMS proxy vlákna. Je platný jenom pro přístup k tomuto rozhraní z proxy vlákno spuštěné na kořenovém adresáři virtuálního procesoru přiřazená plánovače UMS.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[Policyelementkey –](concurrency-namespace-enums.md)<br/>
[IScheduler – struktura](ischeduler-structure.md)<br/>
[IUMSCompletionList – struktura](iumscompletionlist-structure.md)<br/>
[IResourceManager – struktura](iresourcemanager-structure.md)

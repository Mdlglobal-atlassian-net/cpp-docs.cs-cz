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
ms.openlocfilehash: 45df744a9850510006e4bf887c8ed61b000a8e5c
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139997"
---
# <a name="iumsscheduler-structure"></a>Struktura rozhraní IUMSScheduler

Rozhraní pro abstrakci pracovního plánovače, které chce Správce prostředků Concurrency Runtime zaplánovatelná vlákna v uživatelském režimu (UMS). Správce prostředků toto rozhraní používá ke komunikaci s plánovači vláken UMS. Rozhraní `IUMSScheduler` dědí z rozhraní `IScheduler`.

## <a name="syntax"></a>Syntaxe

```cpp
struct IUMSScheduler : public IScheduler;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IUMSScheduler –:: Setcompletionlist –](#setcompletionlist)|Přiřadí rozhraní `IUMSCompletionList` plánovači vláken UMS.|

## <a name="remarks"></a>Poznámky

Pokud implementujete vlastního plánovače, který komunikuje s Správce prostředků a chcete, aby se vlákna UMS do plánovače namísto běžných vláken Win32, měli byste poskytnout implementaci rozhraní `IUMSScheduler`. Kromě toho byste měli nastavit hodnotu zásad pro klíč zásad Scheduler `SchedulerKind` `UmsThreadDefault`. Pokud zásada určuje vlákno UMS, rozhraní `IScheduler`, které je předáno jako parametr metodě [IResourceManager:: registerscheduler –](iresourcemanager-structure.md#registerscheduler) , musí být rozhraní `IUMSScheduler`.

Správce prostředků je možné doUMS vlákna pouze v operačních systémech, které mají funkci UMS. 64 – bitové operační systémy s verzí Windows 7 a vyšší podporují UMS vlákna. Pokud vytvoříte zásadu plánovače s klíčem `SchedulerKind` nastaveným na hodnotu `UmsThreadDefault` a podkladová platforma nepodporuje UMS, hodnota klíče `SchedulerKind` v této zásadě se změní na hodnotu `ThreadScheduler`. Před tím, než očekáváte příjem UMSch vláken, byste měli vždycky číst tuto hodnotu této zásady.

Rozhraní `IUMSScheduler` je jedním z konců obousměrné komunikace mezi plánovačem a Správce prostředků. Druhý konec je reprezentován rozhraním `IResourceManager` a `ISchedulerProxy`, která jsou implementována Správce prostředků.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[IScheduler](ischeduler-structure.md)

`IUMSScheduler`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm. h

**Obor názvů:** souběžnost

## <a name="setcompletionlist"></a>IUMSScheduler –:: Setcompletionlist – – metoda

Přiřadí rozhraní `IUMSCompletionList` plánovači vláken UMS.

```cpp
virtual void SetCompletionList(_Inout_ IUMSCompletionList* pCompletionList) = 0;
```

### <a name="parameters"></a>Parametry

*pCompletionList*<br/>
Rozhraní seznamu dokončení pro Plánovač. Každý Plánovač obsahuje jeden seznam.

### <a name="remarks"></a>Poznámky

Správce prostředků vyvolá tuto metodu v plánovači, který určuje, že chce UMS vlákna, poté, co Plánovač vyžádá počáteční přidělení prostředků. Plánovač může použít rozhraní `IUMSCompletionList` k určení, kdy odblokování proxy vláken UMS bylo odblokováno. Je platný jenom pro přístup k tomuto rozhraní z proxy vlákna, které běží na kořenovém adresáři virtuálního procesoru přiřazeného ke službě UMS Scheduler.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[PolicyElementKey –](concurrency-namespace-enums.md)<br/>
[IScheduler – struktura](ischeduler-structure.md)<br/>
[IUMSCompletionList – struktura](iumscompletionlist-structure.md)<br/>
[IResourceManager – struktura](iresourcemanager-structure.md)

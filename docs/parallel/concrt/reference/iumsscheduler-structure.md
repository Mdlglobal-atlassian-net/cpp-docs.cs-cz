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
ms.openlocfilehash: 70954906122c048e5199a801632626d35a8e3f18
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368087"
---
# <a name="iumsscheduler-structure"></a>Struktura rozhraní IUMSScheduler

Rozhraní pro abstrakce plánovače práce, který chce, aby správce prostředků modulu Runtime souběžnosti předal vlákna s chutným režimem uživatele (UMS). Správce prostředků používá toto rozhraní ke komunikaci s plánovači vláken služby UMS. Rozhraní `IUMSScheduler` dědí z `IScheduler` rozhraní.

## <a name="syntax"></a>Syntaxe

```cpp
struct IUMSScheduler : public IScheduler;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[IUMSScheduler::SetCompletionList](#setcompletionlist)|Přiřadí `IUMSCompletionList` rozhraní plánovači vláken UMS.|

## <a name="remarks"></a>Poznámky

Pokud implementujete vlastní plánovač, který komunikuje se Správcem prostředků a chcete, aby podprocesy Služby Jednotné ho sazbě byly `IUMSScheduler` předány plánovači namísto běžných vláken Win32, měli byste poskytnout implementaci rozhraní. Kromě toho byste měli nastavit hodnotu zásad `SchedulerKind` pro `UmsThreadDefault`klíč zásad plánovače . Pokud zásada určuje vlákno služby `IScheduler` UMS, musí být `IUMSScheduler` rozhraním předaným jako parametr metodě [IResourceManager::RegisterScheduler](iresourcemanager-structure.md#registerscheduler) rozhraní.

Správce prostředků je schopen předat podprocesy Služby UMS pouze v operačních systémech, které mají funkci UMS. 64bitové operační systémy s podprocesy Windows 7 a vyšší podporují vlákna systému UMS. Pokud vytvoříte zásadu plánovače `SchedulerKind` s klíčem `UmsThreadDefault` nastaveným na hodnotu a základní platforma `SchedulerKind` nepodporuje službu UMS, hodnota klíče v této zásadě se změní na hodnotu `ThreadScheduler`. Vždy byste měli přečíst zpět tuto hodnotu zásad před očekává, že obdrží vlákna UMS.

Rozhraní `IUMSScheduler` je jeden konec obousměrného komunikačního kanálu mezi plánovačem a Správcem prostředků. Druhý konec je `IResourceManager` reprezentován `ISchedulerProxy` a rozhraní, které jsou implementovány Správce prostředků.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[IScheduler](ischeduler-structure.md)

`IUMSScheduler`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm.h

**Obor názvů:** souběžnost

## <a name="iumsschedulersetcompletionlist-method"></a><a name="setcompletionlist"></a>IUMSScheduler::Metoda SetCompletionList

Přiřadí `IUMSCompletionList` rozhraní plánovači vláken UMS.

```cpp
virtual void SetCompletionList(_Inout_ IUMSCompletionList* pCompletionList) = 0;
```

### <a name="parameters"></a>Parametry

*seznam dokončení*<br/>
Rozhraní seznamu dokončení pro plánovače. Existuje jeden seznam na plánovače.

### <a name="remarks"></a>Poznámky

Správce prostředků vyvolá tuto metodu na plánovači, který určuje, že chce vlákna Služby UMS poté, co plánovač požádal o počáteční přidělení prostředků. Plánovač můžete použít `IUMSCompletionList` rozhraní k určení, kdy jsou odblokovány servery proxy podprocesů UMS. Je platný pouze pro přístup k tomuto rozhraní z proxy vlákna spuštěného v kořenovém adresáři virtuálního procesoru přiřazeném plánovači služby UMS.

## <a name="see-also"></a>Viz také

[obor názvů souběžnosti](concurrency-namespace.md)<br/>
[Klíč PolicyElement](concurrency-namespace-enums.md)<br/>
[IScheduler – struktura](ischeduler-structure.md)<br/>
[IUMSCompletionList – struktura](iumscompletionlist-structure.md)<br/>
[IResourceManager – struktura](iresourcemanager-structure.md)

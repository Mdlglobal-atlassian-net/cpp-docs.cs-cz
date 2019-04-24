---
title: IResourceManager – struktura
ms.date: 03/27/2019
f1_keywords:
- IResourceManager
- CONCRTRM/concurrency::IResourceManager
- CONCRTRM/concurrency::IResourceManager::IResourceManager::OSVersion
- CONCRTRM/concurrency::IResourceManager::IResourceManager::CreateNodeTopology
- CONCRTRM/concurrency::IResourceManager::IResourceManager::GetAvailableNodeCount
- CONCRTRM/concurrency::IResourceManager::IResourceManager::GetFirstNode
- CONCRTRM/concurrency::IResourceManager::IResourceManager::Reference
- CONCRTRM/concurrency::IResourceManager::IResourceManager::RegisterScheduler
- CONCRTRM/concurrency::IResourceManager::IResourceManager::Release
helpviewer_keywords:
- IResourceManager structure
ms.assetid: 3dd5ec2c-fe53-4121-ae77-1bc1d1167ff4
ms.openlocfilehash: 7afb37fb35040975d6e9471a1d12465e5163fafc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301926"
---
# <a name="iresourcemanager-structure"></a>IResourceManager – struktura

Rozhraní pro správce prostředků modulu Runtime souběžnosti. Toto je rozhraní, díky které plánovači komunikovat s Resource Managerem.

## <a name="syntax"></a>Syntaxe

```
struct IResourceManager;
```

## <a name="members"></a>Členové

### <a name="public-enumerations"></a>Veřejné výčty

|Název|Popis|
|----------|-----------------|
|[IResourceManager::OSVersion](#osversion)|Výčtový typ, který představuje verzi operačního systému.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IResourceManager::CreateNodeTopology](#createnodetopology)|K dispozici jenom v ladění sestavení modulu runtime, tato metoda je zkušebnímu zavěšení navrženým k usnadnění testování výhod Resource Manageru na různé topologie hardwaru, bez nutnosti skutečné hardwarové odpovídající konfiguraci. Prodejní buildy modulu runtime tato metoda vrátí bez provedení jakékoli akce.|
|[IResourceManager::GetAvailableNodeCount](#getavailablenodecount)|Vrátí počet uzlů, které jsou k dispozici na Resource Manager.|
|[IResourceManager::GetFirstNode](#getfirstnode)|Vrátí první uzel v pořadí výčtu definovanými správcem prostředků.|
|[Iresourcemanager::Reference –](#reference)|Zvýší počet odkazů na instanci Resource Manageru.|
|[IResourceManager::RegisterScheduler](#registerscheduler)|Zaregistruje plánovače pomocí Resource Manageru. Po registraci Plánovač byste komunikovat s využitím Resource Manageru `ISchedulerProxy` rozhraní, která je vrácena.|
|[IResourceManager::Release](#release)|Sníží počet odkaz na instanci Resource Manageru. Resource Manager je zničen při jeho počet odkazů dosáhne `0`.|

## <a name="remarks"></a>Poznámky

Použití [createresourcemanager –](concurrency-namespace-functions.md) funkce získat rozhraní na instanci typu singleton Resource Manageru. Metoda zvýší počet odkazů v Resource Manageru a byste měli vyvolat [IResourceManager::Release](#release) metodu pro uvolnění odkazu, jakmile budete hotovi s Resource Managerem. Obvykle každý plánovače, kterou jste vytvořili se vyvolat tuto metodu při vytváření a uvolnit odkaz na Resource Manager vypnut.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IResourceManager`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm.h

**Namespace:** souběžnosti

##  <a name="createnodetopology"></a>  Iresourcemanager::createnodetopology – metoda

K dispozici jenom v ladění sestavení modulu runtime, tato metoda je zkušebnímu zavěšení navrženým k usnadnění testování výhod Resource Manageru na různé topologie hardwaru, bez nutnosti skutečné hardwarové odpovídající konfiguraci. Prodejní buildy modulu runtime tato metoda vrátí bez provedení jakékoli akce.

```
virtual void CreateNodeTopology(
    unsigned int nodeCount,
    _In_reads_(nodeCount) unsigned int* pCoreCount,
    _In_reads_opt_(nodeCount) unsigned int** pNodeDistance,
    _In_reads_(nodeCount) unsigned int* pProcessorGroups) = 0;
```

### <a name="parameters"></a>Parametry

*nodeCount*<br/>
Počet uzlů procesoru se simulované.

*pCoreCount*<br/>
Pole, která určuje počet jader na každém uzlu.

*pNodeDistance*<br/>
Matice zadáním uzel vzdálenost mezi dvěma uzly. Tento parametr může mít hodnotu `NULL`.

*pProcessorGroups*<br/>
Pole, která určuje skupinu procesorů každý uzel patří do.

### <a name="remarks"></a>Poznámky

[invalid_argument –](../../../standard-library/invalid-argument-class.md) je vyvolána, pokud parametr `nodeCount` má hodnotu `0` byla předána, nebo pokud parametr `pCoreCount` má hodnotu `NULL`.

[invalid_operation –](invalid-operation-class.md) je vyvolána, pokud tato metoda je volána, když existují další plánovače v procesu.

##  <a name="getavailablenodecount"></a>  Iresourcemanager::getavailablenodecount – metoda

Vrátí počet uzlů, které jsou k dispozici na Resource Manager.

```
virtual unsigned int GetAvailableNodeCount() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Počet uzlů, které jsou k dispozici na Resource Manager.

##  <a name="getfirstnode"></a>  Iresourcemanager::getfirstnode – metoda

Vrátí první uzel v pořadí výčtu definovanými správcem prostředků.

```
virtual ITopologyNode* GetFirstNode() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

První uzel v pořadí výčtu definovanými správcem prostředků.

##  <a name="osversion"></a>  Iresourcemanager::osversion – výčet

Výčtový typ, který představuje verzi operačního systému.

```
enum OSVersion;
```

##  <a name="reference"></a>  Iresourcemanager::Reference – metoda

Zvýší počet odkazů na instanci Resource Manageru.

```
virtual unsigned int Reference() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Výsledný počet odkazů.

##  <a name="registerscheduler"></a>  Iresourcemanager::registerscheduler – metoda

Zaregistruje plánovače pomocí Resource Manageru. Po registraci Plánovač byste komunikovat s využitím Resource Manageru `ISchedulerProxy` rozhraní, která je vrácena.

```
virtual ISchedulerProxy *RegisterScheduler(
    _Inout_ IScheduler* pScheduler,
    unsigned int version) = 0;
```

### <a name="parameters"></a>Parametry

*pScheduler*<br/>
`IScheduler` Rozhraní pro scheduler k registraci.

*version*<br/>
Verze rozhraní komunikace Plánovač používá ke komunikaci s Resource Managerem. S použitím verze umožňuje Resource Manageru vyvíjí komunikačního rozhraní zároveň vám umožní získat přístup do starší funkce plánovače. Plánovačům, které chcete používat funkce služby Správce prostředků k dispozici v sadě Visual Studio 2010 měli používat verzi `CONCRT_RM_VERSION_1`.

### <a name="return-value"></a>Návratová hodnota

`ISchedulerProxy` Rozhraní Resource Manager je spojen s váš plánovač. Pomocí tohoto rozhraní by měl váš Plánovač komunikovat s využitím Resource Manageru od této chvíle v.

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete zahájit komunikaci se správcem prostředků. Metoda přidruží `IScheduler` rozhraní pro váš Plánovač s `ISchedulerProxy` rozhraní a praktické je zpět. Vrácené rozhraní můžete požádat o spuštění prostředky používají váš Plánovač, nebo k odběru vláken s Resource Managerem. Resource Manager použije zásady prvky z zásadu plánovače vrácené [ischeduler::getpolicy –](ischeduler-structure.md#getpolicy) metodou ke zjištění, jaký typ vlákna Plánovač potřebovat k provedení práce. Pokud vaše `SchedulerKind` má hodnotu klíče zásad `UmsThreadDefault` a přečíst hodnotu zpět z zásady jako hodnota `UmsThreadDefault`, `IScheduler` rozhraní předaný metodě musí být `IUMSScheduler` rozhraní.

Metoda vyvolá `invalid_argument` výjimka Pokud parametr `pScheduler` má hodnotu `NULL` nebo, pokud parametr `version` není platná verze rozhraní komunikace.

##  <a name="release"></a>  IResourceManager::Release – metoda

Sníží počet odkaz na instanci Resource Manageru. Resource Manager je zničen při jeho počet odkazů dosáhne `0`.

```
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Výsledný počet odkazů.

## <a name="see-also"></a>Viz také:

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[ISchedulerProxy – struktura](ischedulerproxy-structure.md)<br/>
[IScheduler – struktura](ischeduler-structure.md)

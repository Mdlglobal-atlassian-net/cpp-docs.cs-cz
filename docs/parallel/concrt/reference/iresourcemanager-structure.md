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
ms.openlocfilehash: 15e27a586fc039791255c01a053f6a1109183f90
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368178"
---
# <a name="iresourcemanager-structure"></a>IResourceManager – struktura

Rozhraní správce prostředků modulu Prostředky modulu Souběžnost Runtime. Toto je rozhraní, pomocí kterého plánovači komunikují se Správcem prostředků.

## <a name="syntax"></a>Syntaxe

```cpp
struct IResourceManager;
```

## <a name="members"></a>Členové

### <a name="public-enumerations"></a>Veřejné výčty

|Name (Název)|Popis|
|----------|-----------------|
|[IResourceManager::OSVersion](#osversion)|Výčtový typ, který představuje verzi operačního systému.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[IResourceManager::CreateNodeTopology](#createnodetopology)|Tato metoda, která je k dispozici pouze v ladicích sestaveních modulu runtime, je testovací mašlovým hákem určeným k usnadnění testování správce prostředků na různých hardwarových topologiích, aniž by bylo nutné, aby skutečný hardware odpovídal konfiguraci. S maloobchodní sestavení runtime, tato metoda se vrátí bez provedení jakékoli akce.|
|[IResourceManager::GetAvailableNodeCount](#getavailablenodecount)|Vrátí počet uzlů, které jsou k dispozici pro Správce prostředků.|
|[IResourceManager::GetFirstNode](#getfirstnode)|Vrátí první uzel v pořadí výčtu podle definice Správce prostředků.|
|[IResourceManager::Reference](#reference)|Inkrementy odkaz na instanci Správce prostředků.|
|[IResourceManager::RegisterScheduler](#registerscheduler)|Zaregistruje plánovače ve Správci prostředků. Jakmile je plánovač zaregistrován, měl by komunikovat `ISchedulerProxy` se Správcem prostředků pomocí rozhraní, které je vráceno.|
|[IResourceManager::Uvolnit](#release)|Sníží počet odkazů na instanci Správce prostředků. Správce prostředků je zničen, když `0`jeho počet odkazů přejde do aplikace .|

## <a name="remarks"></a>Poznámky

Pomocí funkce [CreateResourceManager](concurrency-namespace-functions.md) získáte rozhraní k instanci Správce prostředků singleton. Metoda se nasytí počet odkazů na Správce prostředků a měli byste vyvolat [IResourceManager::Release](#release) metoda uvolnit odkaz, když jste hotovi s Resource Manager. Každý plánovač, který vytvoříte, obvykle vyvolá tuto metodu během vytváření a po jeho vypnutí uvolní odkaz na Správce prostředků.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IResourceManager`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm.h

**Obor názvů:** souběžnost

## <a name="iresourcemanagercreatenodetopology-method"></a><a name="createnodetopology"></a>IResourceManager::Metoda CreateNodedetopology

Tato metoda, která je k dispozici pouze v ladicích sestaveních modulu runtime, je testovací mašlovým hákem určeným k usnadnění testování správce prostředků na různých hardwarových topologiích, aniž by bylo nutné, aby skutečný hardware odpovídal konfiguraci. S maloobchodní sestavení runtime, tato metoda se vrátí bez provedení jakékoli akce.

```cpp
virtual void CreateNodeTopology(
    unsigned int nodeCount,
    _In_reads_(nodeCount) unsigned int* pCoreCount,
    _In_reads_opt_(nodeCount) unsigned int** pNodeDistance,
    _In_reads_(nodeCount) unsigned int* pProcessorGroups) = 0;
```

### <a name="parameters"></a>Parametry

*nodeCount*<br/>
Počet simulovaných uzlů procesoru.

*počet pCoreCount*<br/>
Pole, které určuje počet jader v každém uzlu.

*pNodeDistance*<br/>
Matice určující vzdálenost uzlu mezi libovolnými dvěma uzly. Tento parametr může `NULL`mít hodnotu .

*pSkupiny procesorů*<br/>
Pole, které určuje skupinu procesoru, do které patří každý uzel.

### <a name="remarks"></a>Poznámky

[invalid_argument](../../../standard-library/invalid-argument-class.md) je vyvolána, `nodeCount` pokud `0` parametr má hodnotu byla `pCoreCount` předána, nebo pokud parametr má hodnotu `NULL`.

[invalid_operation](invalid-operation-class.md) je vyvolána, pokud je tato metoda volána, zatímco v procesu existují jiné plánovače.

## <a name="iresourcemanagergetavailablenodecount-method"></a><a name="getavailablenodecount"></a>IResourceManager::Metoda GetAvailableNodeCount

Vrátí počet uzlů, které jsou k dispozici pro Správce prostředků.

```cpp
virtual unsigned int GetAvailableNodeCount() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Počet uzlů, které jsou k dispozici pro Správce prostředků.

## <a name="iresourcemanagergetfirstnode-method"></a><a name="getfirstnode"></a>IResourceManager::Metoda GetFirstNode

Vrátí první uzel v pořadí výčtu podle definice Správce prostředků.

```cpp
virtual ITopologyNode* GetFirstNode() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

První uzel v pořadí výčtu, jak je definováno Správceprostředků.

## <a name="iresourcemanagerosversion-enumeration"></a><a name="osversion"></a>IResourceManager::Výčet verze OSVersion

Výčtový typ, který představuje verzi operačního systému.

```cpp
enum OSVersion;
```

## <a name="iresourcemanagerreference-method"></a><a name="reference"></a>IResourceManager::Reference Method

Inkrementy odkaz na instanci Správce prostředků.

```cpp
virtual unsigned int Reference() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Výsledný počet odkazů.

## <a name="iresourcemanagerregisterscheduler-method"></a><a name="registerscheduler"></a>IResourceManager::Metoda RegisterScheduler

Zaregistruje plánovače ve Správci prostředků. Jakmile je plánovač zaregistrován, měl by komunikovat `ISchedulerProxy` se Správcem prostředků pomocí rozhraní, které je vráceno.

```cpp
virtual ISchedulerProxy *RegisterScheduler(
    _Inout_ IScheduler* pScheduler,
    unsigned int version) = 0;
```

### <a name="parameters"></a>Parametry

*pScheduler*<br/>
Rozhraní `IScheduler` k plánovači, který má být registrován.

*Verze*<br/>
Verze komunikačního rozhraní, kterou plánovač používá ke komunikaci se Správcem prostředků. Použití verze umožňuje Správce prostředků vyvíjet komunikační rozhraní a zároveň umožňuje plánovačům získat přístup ke starším funkcím. Plánovači, kteří chtějí používat funkce Správce prostředků v sadě `CONCRT_RM_VERSION_1`Visual Studio 2010, by měli používat verzi .

### <a name="return-value"></a>Návratová hodnota

Rozhraní `ISchedulerProxy` Správce prostředků přidružené k plánovači. Plánovač by měl používat toto rozhraní ke komunikaci se Správcem prostředků od tohoto okamžiku.

### <a name="remarks"></a>Poznámky

Tato metoda slouží k zahájení komunikace se Správcem prostředků. Metoda přidruží `IScheduler` rozhraní pro plánovač `ISchedulerProxy` s rozhraním a předá ji zpět k vám. Vrácené rozhraní můžete použít k vyžádání prostředků spuštění pro použití plánovačem nebo k odběru vláken se Správcem prostředků. Správce prostředků použije prvky zásad ze zásad plánovače vrácené metodou [IScheduler::GetPolicy](ischeduler-structure.md#getpolicy) k určení typu vláken, která bude plánovač potřebovat k provedení práce. Pokud `SchedulerKind` klíč zásadmá `UmsThreadDefault` hodnotu a hodnota je přečtena zpět `UmsThreadDefault`ze `IScheduler` zásady jako hodnota `IUMSScheduler` , rozhraní předané metodě musí být rozhraní.

Metoda vyvolá `invalid_argument` výjimku, pokud `pScheduler` má `NULL` parametr hodnotu `version` nebo pokud parametr není platnou verzí komunikačního rozhraní.

## <a name="iresourcemanagerrelease-method"></a><a name="release"></a>IResourceManager::Metoda uvolnění

Sníží počet odkazů na instanci Správce prostředků. Správce prostředků je zničen, když `0`jeho počet odkazů přejde do aplikace .

```cpp
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Výsledný počet odkazů.

## <a name="see-also"></a>Viz také

[obor názvů souběžnosti](concurrency-namespace.md)<br/>
[ISchedulerProxy – struktura](ischedulerproxy-structure.md)<br/>
[IScheduler – struktura](ischeduler-structure.md)

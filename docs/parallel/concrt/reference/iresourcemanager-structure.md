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
ms.openlocfilehash: 7ce5b07f5eb4272db1b00b7f0105b790ddbb28fe
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142987"
---
# <a name="iresourcemanager-structure"></a>IResourceManager – struktura

Rozhraní pro Správce prostředků Concurrency Runtime. Toto je rozhraní, podle kterého budou schedulery komunikovat s Správce prostředků.

## <a name="syntax"></a>Syntaxe

```cpp
struct IResourceManager;
```

## <a name="members"></a>Členové

### <a name="public-enumerations"></a>Veřejné výčty

|Název|Popis|
|----------|-----------------|
|[IResourceManager:: OSVersion](#osversion)|Výčtový typ, který představuje verzi operačního systému.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IResourceManager:: Createnodetopology –](#createnodetopology)|K dispozici pouze v ladicích sestaveních modulu runtime je tato metoda testovacím zavěšením navrženým k usnadnění testování Správce prostředků v různých hardwarových topologiích, aniž by bylo potřeba skutečný hardware, který odpovídá konfiguraci. V maloobchodních sestavách modulu runtime bude tato metoda vracet bez provedení jakékoli akce.|
|[IResourceManager:: Getavailablenodecount –](#getavailablenodecount)|Vrátí počet uzlů, které jsou k dispozici pro Správce prostředků.|
|[IResourceManager:: Getfirstnode –](#getfirstnode)|Vrátí první uzel v pořadí vyčíslení, jak je definováno Správce prostředků.|
|[IResourceManager:: Reference](#reference)|Zvýší počet odkazů na instanci Správce prostředků.|
|[IResourceManager:: Registerscheduler –](#registerscheduler)|Zaregistruje Plánovač s Správce prostředků. Po zaregistrování plánovače by měl komunikovat s Správce prostředků pomocí rozhraní `ISchedulerProxy`, které se vrátí.|
|[IResourceManager:: Release](#release)|Sníží počet odkazů na instanci Správce prostředků. Správce prostředků je zničen, pokud je počet odkazů přenesen na `0`.|

## <a name="remarks"></a>Poznámky

Pomocí funkce [CreateResourceManager –](concurrency-namespace-functions.md) můžete získat rozhraní pro instanci typu Singleton správce prostředků. Metoda zvýší počet odkazů na Správce prostředků a měli byste vyvolat metodu [IResourceManager:: Release](#release) pro vydání odkazu, když jste hotovi s správce prostředků. Každý vytvořený Plánovač obvykle během vytváření vyvolá tuto metodu a po vypnutí vydává odkaz na Správce prostředků.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IResourceManager`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm. h

**Obor názvů:** souběžnost

## <a name="createnodetopology"></a>IResourceManager:: Createnodetopology – – metoda

K dispozici pouze v ladicích sestaveních modulu runtime je tato metoda testovacím zavěšením navrženým k usnadnění testování Správce prostředků v různých hardwarových topologiích, aniž by bylo potřeba skutečný hardware, který odpovídá konfiguraci. V maloobchodních sestavách modulu runtime bude tato metoda vracet bez provedení jakékoli akce.

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

*pCoreCount*<br/>
Pole, které určuje počet jader na jednotlivých uzlech.

*pNodeDistance*<br/>
Matice, která určuje vzdálenost uzlu mezi libovolnými dvěma uzly. Tento parametr může mít hodnotu `NULL`.

*pProcessorGroups*<br/>
Pole, které určuje skupinu procesorů, do které každý uzel patří.

### <a name="remarks"></a>Poznámky

[invalid_argument](../../../standard-library/invalid-argument-class.md) je vyvolána, pokud parametr `nodeCount` obsahuje hodnotu `0` byla předána do, nebo pokud parametr `pCoreCount` má hodnotu `NULL`.

[invalid_operation](invalid-operation-class.md) je vyvolána, pokud je tato metoda volána, zatímco jiné plánovače existují v procesu.

## <a name="getavailablenodecount"></a>IResourceManager:: Getavailablenodecount – – metoda

Vrátí počet uzlů, které jsou k dispozici pro Správce prostředků.

```cpp
virtual unsigned int GetAvailableNodeCount() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Počet uzlů, které jsou k dispozici pro Správce prostředků.

## <a name="getfirstnode"></a>IResourceManager:: Getfirstnode – – metoda

Vrátí první uzel v pořadí vyčíslení, jak je definováno Správce prostředků.

```cpp
virtual ITopologyNode* GetFirstNode() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

První uzel v pořadí výčtů, jak je definováno Správce prostředků.

## <a name="osversion"></a>IResourceManager:: OSVersion – výčet

Výčtový typ, který představuje verzi operačního systému.

```cpp
enum OSVersion;
```

## <a name="reference"></a>IResourceManager:: Reference – metoda

Zvýší počet odkazů na instanci Správce prostředků.

```cpp
virtual unsigned int Reference() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Výsledný počet odkazů.

## <a name="registerscheduler"></a>IResourceManager:: Registerscheduler – – metoda

Zaregistruje Plánovač s Správce prostředků. Po zaregistrování plánovače by měl komunikovat s Správce prostředků pomocí rozhraní `ISchedulerProxy`, které se vrátí.

```cpp
virtual ISchedulerProxy *RegisterScheduler(
    _Inout_ IScheduler* pScheduler,
    unsigned int version) = 0;
```

### <a name="parameters"></a>Parametry

*pScheduler*<br/>
Do plánovače je `IScheduler` rozhraní, které se má zaregistrovat.

*version*<br/>
Verze komunikačního rozhraní, které Plánovač používá ke komunikaci s Správce prostředků. Použití verze umožňuje Správce prostředků vyvíjet komunikační rozhraní a zároveň umožňuje plánovači získat přístup ke starším funkcím. Plánovače, které chtějí používat funkce Správce prostředků přítomné v aplikaci Visual Studio 2010, by měly používat `CONCRT_RM_VERSION_1`verze.

### <a name="return-value"></a>Návratová hodnota

Rozhraní `ISchedulerProxy`, které Správce prostředků přidruženo k vašemu plánovači. Váš Plánovač by měl toto rozhraní používat ke komunikaci s Správce prostředků od tohoto okamžiku.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte, chcete-li zahájit komunikaci s Správce prostředků. Metoda přidružuje rozhraní `IScheduler` pro váš Plánovač s rozhraním `ISchedulerProxy` a bude na vás vracet. Vrácené rozhraní můžete použít k vyžádání prostředků spouštění pro použití v Plánovači nebo k přihlášení k odběru vláken pomocí Správce prostředků. Správce prostředků bude používat prvky zásad ze zásad plánovače vrácených metodou [IScheduler:: GetPolicy](ischeduler-structure.md#getpolicy) k určení typu vláken, které bude Plánovač potřebovat k provedení práce. Pokud má klíč zásad `SchedulerKind` hodnotu `UmsThreadDefault` a hodnota je čtena zpět, jako `UmsThreadDefault`hodnoty, `IScheduler` rozhraní předané metodě musí být `IUMSScheduler` rozhraní.

Metoda vyvolá výjimku `invalid_argument`, pokud `pScheduler` parametru má hodnotu `NULL` nebo pokud parametr `version` není platnou verzí pro komunikační rozhraní.

## <a name="release"></a>IResourceManager:: Release – metoda

Sníží počet odkazů na instanci Správce prostředků. Správce prostředků je zničen, pokud je počet odkazů přenesen na `0`.

```cpp
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Výsledný počet odkazů.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[ISchedulerProxy – struktura](ischedulerproxy-structure.md)<br/>
[IScheduler – struktura](ischeduler-structure.md)

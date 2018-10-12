---
title: Context – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- Context
- CONCRT/concurrency::Context
- CONCRT/concurrency::Context::Block
- CONCRT/concurrency::Context::CurrentContext
- CONCRT/concurrency::Context::GetId
- CONCRT/concurrency::Context::GetScheduleGroupId
- CONCRT/concurrency::Context::GetVirtualProcessorId
- CONCRT/concurrency::Context::Id
- CONCRT/concurrency::Context::IsCurrentTaskCollectionCanceling
- CONCRT/concurrency::Context::IsSynchronouslyBlocked
- CONCRT/concurrency::Context::Oversubscribe
- CONCRT/concurrency::Context::ScheduleGroupId
- CONCRT/concurrency::Context::Unblock
- CONCRT/concurrency::Context::VirtualProcessorId
- CONCRT/concurrency::Context::Yield
dev_langs:
- C++
helpviewer_keywords:
- Context class
ms.assetid: c0d553f3-961d-4ecd-9a29-4fa4351673b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 854f5935a66d845aa3c63b9f15857732fdfe6b8a
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163865"
---
# <a name="context-class"></a>Context – třída

Představuje abstrakci pro kontext spuštění.

## <a name="syntax"></a>Syntaxe

```
class Context;
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Název|Popis|
|----------|-----------------|
|[~Context Destructor](#dtor)||

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Blok](#block)|Blokuje aktuální kontext.|
|[CurrentContext](#currentcontext)|Vrací ukazatel na aktuální kontext.|
|[Getid –](#getid)|Vrátí identifikátor kontextu, který je jedinečný v rámci plánovače, do kterého kontext patří.|
|[GetScheduleGroupId](#getschedulegroupid)|Vrátí identifikátor plánu skupiny, kontext aktuálně pracuje.|
|[GetVirtualProcessorId](#getvirtualprocessorid)|Vrátí identifikátor virtuálního procesoru, je kontext aktuálně spuštěn.|
|[ID](#id)|Vrátí identifikátor aktuálního kontextu, který je jedinečný v rámci plánovače, do kterého aktuální kontext patří.|
|[Iscurrenttaskcollectioncanceling –](#iscurrenttaskcollectioncanceling)|Vrátí informace o tom, zda kolekce úkolu, který je právě probíhá vloženě v aktuálním kontextu je uprostřed aktivního rušení (nebo bude za chvíli).|
|[Issynchronouslyblocked –](#issynchronouslyblocked)|Určuje, zda je kontext synchronně blokován. Kontext je považován za synchronně blokovaný, pokud výslovně provedl akci, která vedla k blokování.|
|[Přidělit nadměrnému počtu procesů](#oversubscribe)|Vloží další virtuální procesor do plánovače pro dobu trvání bloku kódu při vyvolání v kontextu spuštění v jednom z virtuálních procesorů v tomto plánovači.|
|[ScheduleGroupId](#schedulegroupid)|Vrátí identifikátor plánu skupiny, aktuální kontext pracuje.|
|[Odblokování](#unblock)|Odblokuje kontext a způsobí, že se stane spustitelným.|
|[VirtualProcessorId](#virtualprocessorid)|Vrátí identifikátor virtuálního procesoru, je aktuální kontext spuštěn.|
|[YIELD](#yield)|Předá vykonávání, takže může vykonávat jiný kontext. Pokud žádný jiný kontext není k dispozici, Plánovač může ustoupit jinému vláknu operačního systému.|

## <a name="remarks"></a>Poznámky

Plánovač Concurrency Runtime (viz [Plánovač](scheduler-class.md)) používá kontexty spuštění k provedení práce ve frontě v aplikaci. Vlákno Win32 je příkladem kontextu spuštění v operačním systému Windows.

Kdykoli se úroveň souběžnosti plánovače rovná počtu virtuálních procesorů poskytnutých správcem prostředků. Virtuální procesor je abstrakcí pro zpracování zdrojů a map pro vlákno hardwaru v podkladovém systému. Pouze jeden kontext plánovače může provádět na virtuální procesor v daném okamžiku.

Plánovač má kooperativní charakter a vykonávající kontext může kdykoliv přinést svůj virtuální procesor do jiného kontextu, pokud přeje přejít do stavu čekání. Když je jeho čekání uspokojeno, nemůže pokračovat, dokud ho dostupný virtuální procesor z plánovače začne, ale jeho spuštění.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Context`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h

**Namespace:** souběžnosti

##  <a name="block"></a> Blok

Blokuje aktuální kontext.

```
static void __cdecl Block();
```

### <a name="remarks"></a>Poznámky

Tato metoda způsobí procesu výchozím plánovačem se vytvoří a/nebo připojené k volání kontextu, pokud neexistuje žádný Plánovač aktuálně přiřazen k volání kontextu.

Pokud volání kontextu běží na virtuální procesor, virtuální procesor najdete jiný spustitelný kontextu spuštění nebo může potenciálně vytvořte novou.

Po `Block` byla volána metoda nebo bude volána, musíte ji spárovat volání [Odblokovat](#unblock) metodu z jiného kontextu spuštění, aby ji znovu spustit. Mějte na paměti, že je mezi bodem, kde váš kód publikuje jeho kontextu pro jiné vlákno, abyste mohli volat kritické době `Unblock` metoda a bodu, kdy Skutečná metoda volání `Block` tvoří. Během tohoto období se nesmějí volat žádné metody, která můžete zase blokovat nebo odblokovat vlastní důvodů (například získání zámku). Volání `Block` a `Unblock` metoda do not track Důvod blokování a odblokování. Vlastnictví by měl mít pouze jeden objekt `Block` -  `Unblock` pár.

Tato metoda může vyvolat výjimky, včetně různých [scheduler_resource_allocation_error –](scheduler-resource-allocation-error-class.md).

##  <a name="dtor"></a> ~ Kontextu

```
virtual ~Context();
```

##  <a name="currentcontext"></a> CurrentContext

Vrací ukazatel na aktuální kontext.

```
static Context* __cdecl CurrentContext();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktuální kontext.

### <a name="remarks"></a>Poznámky

Tato metoda způsobí procesu výchozím plánovačem se vytvoří a/nebo připojené k volání kontextu, pokud neexistuje žádný Plánovač aktuálně přiřazen k volání kontextu.

##  <a name="getid"></a> Getid –

Vrátí identifikátor kontextu, který je jedinečný v rámci plánovače, do kterého kontext patří.

```
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Identifikátor kontextu, který je jedinečný v rámci plánovače, do kterého kontext patří.

##  <a name="getschedulegroupid"></a> Getschedulegroupid –

Vrátí identifikátor plánu skupiny, kontext aktuálně pracuje.

```
virtual unsigned int GetScheduleGroupId() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Identifikátor plánu skupiny kontext aktuálně pracuje.

### <a name="remarks"></a>Poznámky

Vrácená hodnota z této metody je okamžité vzorkování plánu skupiny, který je spuštěn kontextu. Pokud tato metoda je volána v jiném kontextu než kontextu aktuální, hodnota může být zastaralá chvíli se vrátí a nelze spoléhat. Tato metoda se obvykle používá pro ladění nebo pouze pro účely sledování.

##  <a name="getvirtualprocessorid"></a> Getvirtualprocessorid –

Vrátí identifikátor virtuálního procesoru, je kontext aktuálně spuštěn.

```
virtual unsigned int GetVirtualProcessorId() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Pokud je kontext aktuálně spuštěn na virtuální procesor, identifikátor virtuálního procesoru, který je kontext aktuálně spuštěn. v opačném případě hodnota `-1`.

### <a name="remarks"></a>Poznámky

Vrácená hodnota z této metody je okamžité vzorkování virtuálního procesoru, který je spuštěn kontextu. Tato hodnota může být zastaralá chvíli se vrátí a nelze spoléhat. Tato metoda se obvykle používá pro ladění nebo pouze pro účely sledování.

##  <a name="id"></a> ID

Vrátí identifikátor aktuálního kontextu, který je jedinečný v rámci plánovače, do kterého aktuální kontext patří.

```
static unsigned int __cdecl Id();
```

### <a name="return-value"></a>Návratová hodnota

Pokud aktuální kontext je připojena k plánovače, identifikátor pro aktuální kontext, který je jedinečný v rámci plánovače, do kterého patří aktuální kontext; v opačném případě hodnota `-1`.

##  <a name="iscurrenttaskcollectioncanceling"></a> Iscurrenttaskcollectioncanceling –

Vrátí informace o tom, zda kolekce úkolu, který je právě probíhá vloženě v aktuálním kontextu je uprostřed aktivního rušení (nebo bude za chvíli).

```
static bool __cdecl IsCurrentTaskCollectionCanceling();
```

### <a name="return-value"></a>Návratová hodnota

Pokud plánovače je připojen k volání kontextu a skupiny úloh spouští úlohu jako vloženou v tomto kontextu, údaj o tom, zda úkol skupiny je uprostřed aktivního rušení (nebo bude zanedlouho); v opačném případě hodnota `false`.

##  <a name="issynchronouslyblocked"></a> Issynchronouslyblocked –

Určuje, zda je kontext synchronně blokován. Kontext je považován za synchronně blokovaný, pokud výslovně provedl akci, která vedla k blokování.

```
virtual bool IsSynchronouslyBlocked() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Určuje, zda je kontext synchronně blokován.

### <a name="remarks"></a>Poznámky

Kontext je považován za synchronně blokovaný, pokud výslovně provedl akci, která vedla k blokování. V Plánovači vlákno by jít přímého volání `Context::Block` metody nebo objekt synchronizace, které bylo vytvořeno prostřednictvím `Context::Block` metody.

Vrácená hodnota z této metody je okamžité vzorku o tom, zda je kontext synchronně blokován. Tato hodnota může být zastaralá chvíli se vrátí a jde použít jenom za velmi specifických podmínek.

##  <a name="operator_delete"></a> delete – operátor

A `Context` objekt je zničen interně modulem runtime. Nelze odstranit explicitně.

```
void operator delete(void* _PObject);
```

### <a name="parameters"></a>Parametry

*_PObject*<br/>
Ukazatel na objekt, který má být odstraněna.

##  <a name="oversubscribe"></a> Přidělit nadměrnému počtu procesů

Vloží další virtuální procesor do plánovače pro dobu trvání bloku kódu při vyvolání v kontextu spuštění v jednom z virtuálních procesorů v tomto plánovači.

```
static void __cdecl Oversubscribe(bool _BeginOversubscription);
```

### <a name="parameters"></a>Parametry

*_BeginOversubscription*<br/>
Pokud **true**, jako ukazatel toho, že další virtuální procesor přidaly po dobu trvání překryvného odběru. Pokud **false**, jako ukazatel toho, že by měla končit překryvného odběru a by se měly odebrat dříve přidanými virtuálního procesoru.

##  <a name="schedulegroupid"></a> ScheduleGroupId

Vrátí identifikátor plánu skupiny, aktuální kontext pracuje.

```
static unsigned int __cdecl ScheduleGroupId();
```

### <a name="return-value"></a>Návratová hodnota

Pokud aktuální kontext je připojena k plánovače a práci v plánu skupiny, identifikátor pro Plánovač skupině, která je aktuální kontext pracuje na; v opačném případě hodnota `-1`.

##  <a name="unblock"></a> Odblokování

Odblokuje kontext a způsobí, že se stane spustitelným.

```
virtual void Unblock() = 0;
```

### <a name="remarks"></a>Poznámky

Je možné dokonale pro volání `Unblock` předcházet odpovídající volání metody [bloku](#block) metody. Tak dlouho, dokud volání `Block` a `Unblock` metody jsou správně spárované, modul runtime správně zpracovává přirozený závodu o buď řazení. `Unblock` Už před volání `Block` volání jednoduše Neguje působení `Block` volání.

Existuje několik výjimek, které mohou být vyvolány z této metody. Pokud se pokusí kontext volání `Unblock` metoda sám na sobě, [context_self_unblock –](context-self-unblock-class.md) , bude vyvolána výjimka. Pokud volání `Block` a `Unblock` nejsou správně spárované (například dvě volání `Unblock` jsou vytvořené pro kontext, který aktuálně běží), [context_unblock_unbalanced –](context-unblock-unbalanced-class.md) , bude vyvolána výjimka.

Mějte na paměti, že je mezi bodem, kde váš kód publikuje jeho kontextu pro jiné vlákno, abyste mohli volat kritické době `Unblock` metoda a bodu, kdy Skutečná metoda volání `Block` tvoří. Během tohoto období se nesmějí volat žádné metody, která můžete zase blokovat nebo odblokovat vlastní důvodů (například získání zámku). Volání `Block` a `Unblock` metoda do not track Důvod blokování a odblokování. Vlastnictví by měl mít pouze jeden objekt `Block` a `Unblock` pár.

##  <a name="virtualprocessorid"></a> Virtualprocessorid –

Vrátí identifikátor virtuálního procesoru, je aktuální kontext spuštěn.

```
static unsigned int __cdecl VirtualProcessorId();
```

### <a name="return-value"></a>Návratová hodnota

Pokud do fronty plánovače, identifikátor virtuálního procesoru, je aktuální kontext spuštěn; je připojený aktuální kontext v opačném případě hodnota `-1`.

### <a name="remarks"></a>Poznámky

Vrácená hodnota z této metody je okamžité vzorkování virtuálního procesoru, je aktuální kontext spuštěn. Tato hodnota může být zastaralá chvíli se vrátí a nelze spoléhat. Tato metoda se obvykle používá pro ladění nebo pouze pro účely sledování.

##  <a name="yield"></a> YIELD

Předá vykonávání, takže může vykonávat jiný kontext. Pokud žádný jiný kontext není k dispozici, Plánovač může ustoupit jinému vláknu operačního systému.

```
static void __cdecl Yield();
```

### <a name="remarks"></a>Poznámky

Tato metoda způsobí procesu výchozím plánovačem se vytvoří a/nebo připojené k volání kontextu, pokud neexistuje žádný Plánovač aktuálně přiřazen k volání kontextu.

##  <a name="yieldexecution"></a> YieldExecution

Předá vykonávání, takže může vykonávat jiný kontext. Pokud žádný jiný kontext není k dispozici, Plánovač může ustoupit jinému vláknu operačního systému.

```
static void __cdecl YieldExecution();
```

### <a name="remarks"></a>Poznámky

Tato metoda způsobí procesu výchozím plánovačem se vytvoří a/nebo připojené k volání kontextu, pokud neexistuje žádný Plánovač aktuálně přiřazen k volání kontextu.

Tato funkce je nového v sadě Visual Studio 2015 a je stejný jako [Yield](#yield) fungovat, ale není v konfliktu s Yield – makro v Windows.h.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[Scheduler – třída](scheduler-class.md)<br/>
[Plánovač úloh](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)


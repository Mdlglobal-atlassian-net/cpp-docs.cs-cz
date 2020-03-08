---
title: Context – třída
ms.date: 11/04/2016
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
helpviewer_keywords:
- Context class
ms.assetid: c0d553f3-961d-4ecd-9a29-4fa4351673b8
ms.openlocfilehash: 7c47d9db64b0af7d5413abed3f85e9d41a591fa2
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865486"
---
# <a name="context-class"></a>Context – třída

Představuje abstrakci pro kontext spuštění.

## <a name="syntax"></a>Syntaxe

```cpp
class Context;
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Název|Popis|
|----------|-----------------|
|[~ Kontextový destruktor](#dtor)||

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Blok](#block)|Blokuje aktuální kontext.|
|[CurrentContext](#currentcontext)|Vrátí ukazatel na aktuální kontext.|
|[GetId –](#getid)|Vrátí identifikátor kontextu, který je jedinečný v rámci plánovače, do kterého patří kontext.|
|[Getschedulegroupid –](#getschedulegroupid)|Vrátí identifikátor skupiny plánů, na které kontext aktuálně pracuje.|
|[Getvirtualprocessorid –](#getvirtualprocessorid)|Vrátí identifikátor virtuálního procesoru, na kterém je kontext aktuálně spuštěn.|
|[ID](#id)|Vrátí identifikátor aktuálního kontextu, který je jedinečný v rámci plánovače, do kterého patří aktuální kontext.|
|[Iscurrenttaskcollectioncanceling –](#iscurrenttaskcollectioncanceling)|Vrátí informaci o tom, zda kolekce úloh, která aktuálně provádí inlineing v aktuálním kontextu, je v průběhu aktivního zrušení (nebo bude brzy).|
|[Issynchronouslyblocked –](#issynchronouslyblocked)|Určuje, zda je kontext synchronně blokován. Kontext je považován za synchronní zablokovaný, pokud explicitně provedl akci, která vedla k blokování.|
|[Oversubscribe –](#oversubscribe)|Vloží další virtuální procesor do plánovače po dobu trvání bloku kódu při vyvolání v kontextu, který je spuštěn na jednom z virtuálních procesorů v daném plánovači.|
|[Schedulegroupid –](#schedulegroupid)|Vrátí identifikátor pro skupinu plánů, na které aktuální kontext pracuje.|
|[Ruší](#unblock)|Odblokuje kontext a způsobí, že se změní na spustitelný.|
|[Virtualprocessorid –](#virtualprocessorid)|Vrátí identifikátor virtuálního procesoru, na kterém je spuštěn aktuální kontext.|
|[Výsledkem](#yield)|Poskytne provádění, aby se mohl spustit jiný kontext. Pokud není k dispozici žádný jiný kontext k získání, může Plánovač získat jiné vlákno operačního systému.|

## <a name="remarks"></a>Poznámky

Plánovač Concurrency Runtime (viz [Scheduler](scheduler-class.md)) používá kontexty spuštění k provedení práce, kterou do fronty přiřadí vaše aplikace. Vlákno Win32 je příkladem kontextu spuštění v operačním systému Windows.

V každém okamžiku se úroveň souběžnosti plánovače rovná počtu virtuálních procesorů, které mu Správce prostředků udělily. Virtuální procesor představuje abstrakci pro zpracování prostředku a mapuje se na hardwarové vlákno v podkladovém systému. U virtuálního procesoru v daném okamžiku může běžet pouze jeden kontext plánovače.

Plánovač je v podstatě společný a vykonávající kontext může kdykoli vracet svůj virtuální procesor do jiného kontextu, pokud chce zadat čekací stav. Když je jeho čekání splněno, nemůže pokračovat, dokud nespustí dostupný virtuální procesor od plánovače.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Context`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ConcRT. h

**Obor názvů:** souběžnost

## <a name="block"></a>Blokované

Blokuje aktuální kontext.

```cpp
static void __cdecl Block();
```

### <a name="remarks"></a>Poznámky

Tato metoda způsobí, že se vytvoří výchozí Plánovač procesu a/nebo připojí se k volajícímu kontextu, pokud není momentálně k volajícímu kontextu přidružen žádný Plánovač.

Pokud je volající kontext spuštěný ve virtuálním procesoru, virtuální procesor najde jiný spustitelný kontext, který se má spustit, nebo může vytvořit nový.

Poté, co byla volána metoda `Block` nebo bude volána, je nutné ji spárovat s voláním metody [odblokování](#unblock) z jiného kontextu spuštění, aby ji bylo možné spustit znovu. Mějte na paměti, že existuje kritické období mezi bodem, kde váš kód publikuje svůj kontext pro jiné vlákno, aby mohl volat metodu `Unblock` a místo, kde se provádí vlastní volání metody `Block`. Během této doby nesmíte volat žádnou metodu, která by mohla zablokovat a odblokovat z vlastních důvodů (například získání zámku). Volání metody `Block` a `Unblock` nesledují důvod pro blokování a odblokování. Vlastnictví `Block`- `Unblock` páry by mělo mít pouze jeden objekt.

Tato metoda může vyvolat nejrůznější výjimky, včetně [scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md).

## <a name="dtor"></a>~ Kontext

```cpp
virtual ~Context();
```

## <a name="currentcontext"></a>CurrentContext

Vrátí ukazatel na aktuální kontext.

```cpp
static Context* __cdecl CurrentContext();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktuální kontext.

### <a name="remarks"></a>Poznámky

Tato metoda způsobí, že se vytvoří výchozí Plánovač procesu a/nebo připojí se k volajícímu kontextu, pokud není momentálně k volajícímu kontextu přidružen žádný Plánovač.

## <a name="getid"></a>GetId –

Vrátí identifikátor kontextu, který je jedinečný v rámci plánovače, do kterého patří kontext.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Identifikátor kontextu, který je jedinečný v rámci plánovače, do kterého patří kontext.

## <a name="getschedulegroupid"></a>Getschedulegroupid –

Vrátí identifikátor skupiny plánů, na které kontext aktuálně pracuje.

```cpp
virtual unsigned int GetScheduleGroupId() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Identifikátor pro skupinu plánu, na níž kontext aktuálně pracuje.

### <a name="remarks"></a>Poznámky

Návratová hodnota z této metody je okamžitý odběr vzorkování skupiny plánování, na které je kontext spuštěn. Pokud je tato metoda volána v jiném kontextu, než je aktuální kontext, hodnota může být zastaralá na okamžik, kdy je vrácena a nelze na ni spoléhat. Tato metoda se obvykle používá pouze pro účely ladění nebo trasování.

## <a name="getvirtualprocessorid"></a>Getvirtualprocessorid –

Vrátí identifikátor virtuálního procesoru, na kterém je kontext aktuálně spuštěn.

```cpp
virtual unsigned int GetVirtualProcessorId() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Pokud je kontext aktuálně spuštěn na virtuálním procesoru, identifikátor virtuálního procesoru, na kterém je kontext aktuálně spuštěn; v opačném případě hodnota `-1`.

### <a name="remarks"></a>Poznámky

Návratovou hodnotou z této metody je okamžitý odběr vzorků virtuálního procesoru, na kterém je spuštěný kontext. Tato hodnota může být zastaralá na okamžik, kdy se vrátí, a nelze na ni spoléhat. Tato metoda se obvykle používá pouze pro účely ladění nebo trasování.

## <a name="id"></a>Účet

Vrátí identifikátor aktuálního kontextu, který je jedinečný v rámci plánovače, do kterého patří aktuální kontext.

```cpp
static unsigned int __cdecl Id();
```

### <a name="return-value"></a>Návratová hodnota

Pokud je aktuální kontext připojen ke Scheduleru, identifikátor aktuálního kontextu, který je jedinečný v rámci plánovače, do kterého patří aktuální kontext; v opačném případě hodnota `-1`.

## <a name="iscurrenttaskcollectioncanceling"></a>Iscurrenttaskcollectioncanceling –

Vrátí informaci o tom, zda kolekce úloh, která aktuálně provádí inlineing v aktuálním kontextu, je v průběhu aktivního zrušení (nebo bude brzy).

```cpp
static bool __cdecl IsCurrentTaskCollectionCanceling();
```

### <a name="return-value"></a>Návratová hodnota

Pokud je Plánovač připojen ke volajícímu kontextu a skupina úloh spouští úlohu vloženou v daném kontextu, uvede se údaj, zda je tato skupina úloh v průběhu aktivního zrušení (nebo brzy bude). v opačném případě hodnota `false`.

## <a name="issynchronouslyblocked"></a>Issynchronouslyblocked –

Určuje, zda je kontext synchronně blokován. Kontext je považován za synchronní zablokovaný, pokud explicitně provedl akci, která vedla k blokování.

```cpp
virtual bool IsSynchronouslyBlocked() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Zda je kontext synchronně blokován.

### <a name="remarks"></a>Poznámky

Kontext je považován za synchronní zablokovaný, pokud explicitně provedl akci, která vedla k blokování. V Plánovači vláken to by znamenalo přímé volání metody `Context::Block` nebo objektu synchronizace, který byl vytvořen pomocí metody `Context::Block`.

Návratová hodnota z této metody je okamžitý vzorek, zda je kontext synchronně blokován. Tato hodnota může být zastaralá, okamžik se vrátí a dá se použít jenom za velmi specifických podmínek.

## <a name="operator_delete"></a>delete – operátor

Objekt `Context` je interně zničen modulem runtime. Nemůžete ji explicitně odstranit.

```cpp
void operator delete(void* _PObject);
```

### <a name="parameters"></a>Parametry

*_PObject*<br/>
Ukazatel na objekt, který má být odstraněn.

## <a name="oversubscribe"></a>Oversubscribe –

Vloží další virtuální procesor do plánovače po dobu trvání bloku kódu při vyvolání v kontextu, který je spuštěn na jednom z virtuálních procesorů v daném plánovači.

```cpp
static void __cdecl Oversubscribe(bool _BeginOversubscription);
```

### <a name="parameters"></a>Parametry

*_BeginOversubscription*<br/>
Je-li **nastavena hodnota true**, je nutné přidat do doby trvání předaného předplatného další virtuální procesor. Pokud má **hodnotu false**, musí se vyznačit, že by mělo dojít k ukončení předplatného a aby se odebral dříve přidaný virtuální procesor.

## <a name="schedulegroupid"></a>Schedulegroupid –

Vrátí identifikátor pro skupinu plánů, na které aktuální kontext pracuje.

```cpp
static unsigned int __cdecl ScheduleGroupId();
```

### <a name="return-value"></a>Návratová hodnota

Pokud je aktuální kontext připojen ke Scheduleru a pracuje na skupině plánů, identifikátor skupiny plánovače, na které aktuální kontext pracuje; v opačném případě hodnota `-1`.

## <a name="unblock"></a>Ruší

Odblokuje kontext a způsobí, že se změní na spustitelný.

```cpp
virtual void Unblock() = 0;
```

### <a name="remarks"></a>Poznámky

Je zcela legální pro volání metody `Unblock` k tomu, aby bylo možné přijít před odpovídajícím voláním metody [Block](#block) . Pokud jsou volání metod `Block` a `Unblock` správně spárována, modul runtime správně zpracovává přirozený závod obou řazení. Volání `Unblock`, které přichází před voláním `Block`, jednoduše negaci efektu volání `Block`.

Existuje několik výjimek, které mohou být vyvolány z této metody. Pokud se kontext pokusí zavolat metodu `Unblock` sám na sebe, bude vyvolána výjimka [context_self_unblock](context-self-unblock-class.md) . Pokud nejsou volání `Block` a `Unblock` správně spárována (například dvě volání `Unblock` jsou vytvořena pro kontext, který je aktuálně spuštěn), bude vyvolána výjimka [context_unblock_unbalanced](context-unblock-unbalanced-class.md) .

Mějte na paměti, že existuje kritické období mezi bodem, kde váš kód publikuje svůj kontext pro jiné vlákno, aby mohl volat metodu `Unblock` a místo, kde se provádí vlastní volání metody `Block`. Během této doby nesmíte volat žádnou metodu, která by mohla zablokovat a odblokovat z vlastních důvodů (například získání zámku). Volání metody `Block` a `Unblock` nesledují důvod pro blokování a odblokování. Vlastnictví `Block` a `Unblock` páru by mělo mít pouze jeden objekt.

## <a name="virtualprocessorid"></a>Virtualprocessorid –

Vrátí identifikátor virtuálního procesoru, na kterém je spuštěn aktuální kontext.

```cpp
static unsigned int __cdecl VirtualProcessorId();
```

### <a name="return-value"></a>Návratová hodnota

Pokud je aktuální kontext připojen ke Scheduleru, identifikátor virtuálního procesoru, na kterém je spuštěn aktuální kontext; v opačném případě hodnota `-1`.

### <a name="remarks"></a>Poznámky

Návratová hodnota z této metody je okamžitý odběr vzorkování virtuálního procesoru, na kterém je spuštěn aktuální kontext. Tato hodnota může být zastaralá na okamžik, kdy se vrátí, a nelze na ni spoléhat. Tato metoda se obvykle používá pouze pro účely ladění nebo trasování.

## <a name="yield"></a>Výsledkem

Poskytne provádění, aby se mohl spustit jiný kontext. Pokud není k dispozici žádný jiný kontext k získání, může Plánovač získat jiné vlákno operačního systému.

```cpp
static void __cdecl Yield();
```

### <a name="remarks"></a>Poznámky

Tato metoda způsobí, že se vytvoří výchozí Plánovač procesu a/nebo připojí se k volajícímu kontextu, pokud není momentálně k volajícímu kontextu přidružen žádný Plánovač.

## <a name="yieldexecution"></a>YieldExecution

Poskytne provádění, aby se mohl spustit jiný kontext. Pokud není k dispozici žádný jiný kontext k získání, může Plánovač získat jiné vlákno operačního systému.

```cpp
static void __cdecl YieldExecution();
```

### <a name="remarks"></a>Poznámky

Tato metoda způsobí, že se vytvoří výchozí Plánovač procesu a/nebo připojí se k volajícímu kontextu, pokud není momentálně k volajícímu kontextu přidružen žádný Plánovač.

Tato funkce je v aplikaci Visual Studio 2015 novinkou a je shodná s funkcí [yield](#yield) , ale není v konfliktu s makrem yield v systému Windows. h.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[Scheduler – třída](scheduler-class.md)<br/>
[Plánovač úloh](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)

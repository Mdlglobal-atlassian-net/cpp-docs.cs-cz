---
title: IThreadProxy – struktura
ms.date: 11/04/2016
f1_keywords:
- IThreadProxy
- CONCRTRM/concurrency::IThreadProxy
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::GetId
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::SwitchOut
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::SwitchTo
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::YieldToSystem
helpviewer_keywords:
- IThreadProxy structure
ms.assetid: feb89241-a555-4e61-ad48-40add54daeca
ms.openlocfilehash: b87694393af4634ec97d05070aa5513cd132098a
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417157"
---
# <a name="ithreadproxy-structure"></a>IThreadProxy – struktura

Abstrakce pro vlákno provádění. V závislosti na klíči zásad `SchedulerType` plánovače, který vytvoříte, vám Správce prostředků udělí proxy vlákna, které je zajištěné buď regulárním vláknem Win32, nebo podprocesem plánovatelná (UMS) v uživatelském režimu. UMS vlákna jsou podporována v 64 operačních systémech s verzí Windows 7 a vyšší.

## <a name="syntax"></a>Syntaxe

```cpp
struct IThreadProxy;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IThreadProxy:: getId –](#getid)|Vrátí jedinečný identifikátor proxy vlákna.|
|[IThreadProxy:: Switch](#switchout)|Zruší přidružení kontextu k základnímu kořenu virtuálního procesoru.|
|[IThreadProxy:: SwitchTo –](#switchto)|Provede přepnutí kontextu družstva z aktuálně spuštěného kontextu do jiného.|
|[IThreadProxy:: YieldToSystem –](#yieldtosystem)|Způsobí, že volající vlákno zaznamená provádění do jiného vlákna, které je připraveno ke spuštění na aktuálním procesoru. Operační systém vybírá další vlákno, které se má provést.|

## <a name="remarks"></a>Poznámky

Proxy vlákna jsou propojena s kontexty spuštění, které jsou reprezentovány rozhraním `IExecutionContext` jako způsob odesílání práce.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IThreadProxy`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm. h

**Obor názvů:** souběžnost

## <a name="getid"></a>IThreadProxy:: getId – – metoda

Vrátí jedinečný identifikátor proxy vlákna.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Jedinečný celočíselný identifikátor.

## <a name="switchout"></a>IThreadProxy:: Switch – metoda

Zruší přidružení kontextu k základnímu kořenu virtuálního procesoru.

```cpp
virtual void SwitchOut(SwitchingProxyState switchState = Blocking) = 0;
```

### <a name="parameters"></a>Parametry

*switchState*<br/>
Určuje stav proxy vlákna, které spouští přepínač. Parametr je typu `SwitchingProxyState`.

### <a name="remarks"></a>Poznámky

Pokud potřebujete zrušit přidružení kontextu od kořene virtuálního procesoru, na kterém je spuštěný, z jakéhokoli důvodu použijte `SwitchOut`. V závislosti na hodnotě předané parametru `switchState`a bez ohledu na to, zda je prováděna v kořenovém adresáři virtuálního procesoru, volání vrátí buď okamžitě, nebo zablokuje proxy vlákna přidruženého k tomuto kontextu. Je-li volána `SwitchOut` s parametrem nastaveným na hodnotu `Idle`, jedná se o chybu. Výsledkem bude [invalid_argument](../../../standard-library/invalid-argument-class.md) výjimka.

`SwitchOut` je užitečné, pokud chcete snížit počet kořenových adresářů virtuálních procesorů, které má váš Plánovač, buď protože vám Správce prostředků na to, že jste to udělali, nebo proto, že jste si vyžádali dočasný kořen virtuálního procesoru, na který jste se dohlásili, a s ním se dokončí. V takovém případě byste měli vyvolat metodu [IVirtualProcessorRoot:: Remove](iexecutionresource-structure.md#remove) v kořenovém adresáři virtuálního procesoru před provedením volání `SwitchOut` s parametrem `switchState` nastaveným na `Blocking`. Tím se zablokuje proxy vlákna a bude pokračovat v provádění, pokud je k dispozici jiný kořen virtuálního procesoru v plánovači. Proxy blokujícího vlákna lze obnovit voláním funkce `SwitchTo` pro přepnutí na kontext spuštění tohoto proxy vlákna. Můžete také obnovit proxy vlákna pomocí jeho přidruženého kontextu a aktivovat tak kořenový adresář virtuálního procesoru. Další informace o tom, jak to provést, naleznete v tématu [IVirtualProcessorRoot:: Activate](ivirtualprocessorroot-structure.md#activate).

`SwitchOut` můžete použít i v případě, že chcete virtuální procesor znovu inicializovat, aby se mohl aktivovat v budoucnu, a to buď blokováním proxy vlákna, nebo jeho dočasným odpojením od kořene virtuálního procesoru, na kterém je spuštěný, a plánovače, pro který odesílá práci. Pokud chcete blokovat proxy vlákna, použijte `SwitchOut` s parametrem `switchState` nastaveným na `Blocking`. Můžete ho později obnovit pomocí `SwitchTo` nebo `IVirtualProcessorRoot::Activate`, jak je uvedeno výše. Použijte `SwitchOut` s parametrem nastaveným na `Nesting`, pokud chcete dočasně odpojit toto proxy vlákna od kořene virtuálního procesoru, na kterém je spuštěný, a plánovače, ke kterému je přidružen virtuální procesor. Volání `SwitchOut` s parametrem `switchState` nastaveným na `Nesting` při jeho spuštění v kořenu virtuálního procesoru způsobí opětovnou inicializaci kořenového adresáře a aktuální proxy vlákna, aby bylo možné pokračovat v provádění bez nutnosti pro jeden. Proxy vlákna se považuje za podobu plánovače, dokud nevolá metodu [IThreadProxy:: Switch](#switchout) s `Blocking` v pozdějším okamžiku. Druhé volání `SwitchOut` s parametrem nastaveným na `Blocking` je určeno pro návrat kontextu do blokovaného stavu, aby jej bylo možné obnovit buď `SwitchTo` nebo `IVirtualProcessorRoot::Activate` v plánovači, ze kterého se odpojila. Vzhledem k tomu, že se neprovádí v kořenu virtuálního procesoru, nebude provedena žádná opětovná inicializace.

Nově inicializovaný kořen virtuálního procesoru se neliší od značky nového kořene virtuálního procesoru, který byl plánovačem udělen Správce prostředků. Můžete ji použít ke spuštění aktivací pomocí kontextu spuštění pomocí `IVirtualProcessorRoot::Activate`.

`SwitchOut` musí být volána na rozhraní `IThreadProxy`, které představuje aktuálně spuštěné vlákno, nebo jsou výsledky nedefinovány.

V knihovnách a hlavičkách, které byly dodávány se sadou Visual Studio 2010, tato metoda nepřijala parametr a neinicializuje kořen virtuálního procesoru. Aby se zachovalo staré chování, zadala se výchozí hodnota parametru `Blocking`.

## <a name="switchto"></a>IThreadProxy:: SwitchTo – – metoda

Provede přepnutí kontextu družstva z aktuálně spuštěného kontextu do jiného.

```cpp
virtual void SwitchTo(
    _Inout_ IExecutionContext* pContext,
    SwitchingProxyState switchState) = 0;
```

### <a name="parameters"></a>Parametry

*pContext*<br/>
Kontext spuštění pro kooperativní přepnutí na.

*switchState*<br/>
Určuje stav proxy vlákna, které spouští přepínač. Parametr je typu `SwitchingProxyState`.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte, chcete-li přepnout z jednoho kontextu spuštění do jiného, z metody [IExecutionContext::D](iexecutioncontext-structure.md#dispatch) ' prvního kontextu spuštění. Metoda přidruží kontext spuštění `pContext` k proxy vlákna, pokud ještě není přidružena k jednomu. Vlastnictví aktuálního proxy vlákna je určeno hodnotou, kterou zadáte v argumentu `switchState`.

Použijte hodnotu `Idle`, pokud chcete vrátit aktuálně spuštěné proxy vlákna do Správce prostředků. Volání `SwitchTo` s parametrem `switchState` nastaveným na `Idle` způsobí, že kontext spuštění `pContext` spuštění na podkladovém prostředku spuštění. Vlastnictví tohoto proxy vlákna se přenáší do Správce prostředků a za účelem dokončení přenosu se očekává, že se hned po `SwitchTo` vrátí, že se vrátíte z `Dispatch` metody kontextu spuštění. Kontext spuštění, který proxy vlákna odeslal, je zrušením přidružení od proxy vlákna a Scheduler ho bude moct znovu použít nebo zničit, jak se podle potřeby dohlíží.

Použijte hodnotu `Blocking`, pokud chcete, aby tento proxy vlákna zadal blokovaný stav. Volání `SwitchTo` s parametrem `switchState` nastaveným na `Blocking` způsobí, že kontext spuštění `pContext` spustí spuštění a zablokuje aktuální proxy vlákna, dokud nebude obnoven. Pokud je proxy vlákna ve stavu `Blocking`, Scheduler zachová vlastnictví proxy vlákna. Proxy blokujícího vlákna lze obnovit voláním funkce `SwitchTo` pro přepnutí na kontext spuštění tohoto proxy vlákna. Můžete také obnovit proxy vlákna pomocí jeho přidruženého kontextu a aktivovat tak kořenový adresář virtuálního procesoru. Další informace o tom, jak to provést, naleznete v tématu [IVirtualProcessorRoot:: Activate](ivirtualprocessorroot-structure.md#activate).

Použijte `Nesting` hodnoty, pokud chcete dočasně odpojit toto proxy vlákna od kořene virtuálního procesoru, na kterém je spuštěný, a plánovače, pro který pracovní postup odesílá. Volání `SwitchTo` s parametrem `switchState` nastaveným na `Nesting` způsobí, že kontext spuštění `pContext` spuštění a aktuální proxy server vlákna také pokračuje ve spouštění bez nutnosti kořene virtuálního procesoru. Proxy vlákno je považováno za to, že opustí Plánovač, dokud nevolá metodu [IThreadProxy:: Switching](#switchout) v pozdějším okamžiku. Metoda `IThreadProxy::SwitchOut` by mohla blokovat proxy vlákna, dokud není k dispozici kořen virtuálního procesoru k jeho naplánování.

`SwitchTo` musí být volána na rozhraní `IThreadProxy`, které představuje aktuálně spuštěné vlákno, nebo jsou výsledky nedefinovány. Funkce vyvolá `invalid_argument`, pokud je parametr `pContext` nastaven na `NULL`.

## <a name="yieldtosystem"></a>IThreadProxy:: YieldToSystem – – metoda

Způsobí, že volající vlákno zaznamená provádění do jiného vlákna, které je připraveno ke spuštění na aktuálním procesoru. Operační systém vybírá další vlákno, které se má provést.

```cpp
virtual void YieldToSystem() = 0;
```

### <a name="remarks"></a>Poznámky

Když je volána proxy vlákna, které je zajištěno běžným vláknem systému Windows, `YieldToSystem` se chová stejně jako `SwitchToThread`funkcí systému Windows. Nicméně při volání z vlákna v uživatelském režimu plánovatelná (UMS), funkce `SwitchToThread` deleguje úkol vyzvednutí dalšího vlákna ke spuštění do plánovače uživatelského režimu, nikoli z operačního systému. Chcete-li dosáhnout požadovaného účinku přepnutí do jiného připraveného vlákna v systému, použijte `YieldToSystem`.

`YieldToSystem` musí být volána na rozhraní `IThreadProxy`, které představuje aktuálně spuštěné vlákno, nebo jsou výsledky nedefinovány.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[IExecutionContext – struktura](iexecutioncontext-structure.md)<br/>
[IScheduler – struktura](ischeduler-structure.md)<br/>
[IVirtualProcessorRoot – struktura](ivirtualprocessorroot-structure.md)

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
ms.openlocfilehash: fc2fb2df06225a5c963fe39178c1b4a10f77953d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368133"
---
# <a name="ithreadproxy-structure"></a>IThreadProxy – struktura

Abstrakce pro vlákno provádění. V závislosti `SchedulerType` na klíč zásad plánovače, který vytvoříte, správce prostředků udělí proxy podproces, který je zálohován buď běžné vlákno Win32 nebo user-mode schedulable (UMS) vlákno. Vlákna služby UMS jsou podporována v 64bitových operačních systémech s verzí Windows 7 a vyšší.

## <a name="syntax"></a>Syntaxe

```cpp
struct IThreadProxy;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[IThreadProxy::GetId](#getid)|Vrátí jedinečný identifikátor proxy vlákna.|
|[iThreadProxy::Přepnutí](#switchout)|Odpojí kontext od kořenového kořene virtuálního procesoru.|
|[iThreadProxy::Přepnout](#switchto)|Provede kooperativní přepnutí kontextu z aktuálně spuštěného kontextu do jiného kontextu.|
|[iThreadProxy::YieldToSystem](#yieldtosystem)|Způsobí, že volající vlákno výnos spuštění do jiného vlákna, který je připraven ke spuštění na aktuální procesor. Operační systém vybere další vlákno, které má být provedeno.|

## <a name="remarks"></a>Poznámky

Proxy vlákna jsou spojeny s kontexty `IExecutionContext` spuštění reprezentované rozhraní jako prostředek expedice práce.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IThreadProxy`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm.h

**Obor názvů:** souběžnost

## <a name="ithreadproxygetid-method"></a><a name="getid"></a>IThreadProxy::Metoda GetId

Vrátí jedinečný identifikátor proxy vlákna.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Jedinečný identifikátor celého čísla.

## <a name="ithreadproxyswitchout-method"></a><a name="switchout"></a>iThreadProxy::Metoda přepnutí

Odpojí kontext od kořenového kořene virtuálního procesoru.

```cpp
virtual void SwitchOut(SwitchingProxyState switchState = Blocking) = 0;
```

### <a name="parameters"></a>Parametry

*switchState*<br/>
Označuje stav proxy vlákna, který provádí přepínač. Parametr je typu `SwitchingProxyState`.

### <a name="remarks"></a>Poznámky

Použijte, `SwitchOut` pokud potřebujete zrušit přidružení kontextu od kořene virtuálního procesoru, ve které je spuštěn, z jakéhokoli důvodu. V závislosti na hodnotě, `switchState`kterou předáte parametru , a na tom, zda je či není spuštěn v kořenovém adresáři virtuálního procesoru, se volání vrátí okamžitě nebo zablokuje proxy vlákna přidruženého k kontextu. Volání `SwitchOut` s parametrem nastaveným na `Idle`. Pokud tak učiníte, bude [invalid_argument](../../../standard-library/invalid-argument-class.md) výjimka.

`SwitchOut`Je užitečné, pokud chcete snížit počet kořenů virtuálního procesoru, které má plánovač, buď proto, že správce prostředků vás k tomu dal pokyn, nebo proto, že jste požádali o dočasný kořen virtuálního procesoru a jste s ním hotovi. V takovém případě byste měli vyvolat metodu [IVirtualProcessorRoot::Remove](iexecutionresource-structure.md#remove) v kořenovém `switchState` adresáři `Blocking`virtuálního procesoru, před voláním `SwitchOut` s parametrem nastaveným na . Tím se zablokuje proxy podprocesu a bude pokračovat v provádění, když je k dispozici jiný kořen virtuálního procesoru v plánovači k jeho spuštění. Blokující proxy podproces lze obnovit `SwitchTo` voláním funkce přepnout do kontextu spuštění tohoto vlákna proxy. Můžete také obnovit proxy vlákna pomocí jeho přidruženého kontextu k aktivaci kořenového adresáře virtuálního procesoru. Další informace o tom, jak to provést, naleznete v [tématu IVirtualProcessorRoot::Activate](ivirtualprocessorroot-structure.md#activate).

`SwitchOut`může být také použit, pokud chcete znovu inicializovat virtuální procesor, takže může být aktivován v budoucnu při blokování proxy podprocesu nebo dočasně odpojení od kořene virtuálního procesoru, na kterém je spuštěn, a plánovač, pro který odesílá práci. Použijte `SwitchOut` s `switchState` parametrem `Blocking` nastaveným na, pokud chcete blokovat proxy vlákna. To může být později `SwitchTo` `IVirtualProcessorRoot::Activate` obnovena pomocí buď nebo jak je uvedeno výše. Použijte `SwitchOut` s parametrem `Nesting` nastaveným na, pokud chcete dočasně odpojit tento proxy podproces od kořenového adresáře virtuálního procesoru, ve kterém je spuštěn, a plánovač, ke kterém je virtuální procesor přidružen. Volání `SwitchOut` s `switchState` parametrem `Nesting` nastaveným na při provádění v kořenovém adresáři virtuálního procesoru způsobí, že kořen bude znovu inicializován a aktuální proxy podproces bude pokračovat v provádění bez nutnosti. Proxy podproces udává, že opustil plánovač, dokud nezavolá metodu `Blocking` [IThreadProxy::SwitchOut](#switchout) později v čase. Druhé volání `SwitchOut` s parametrem `Blocking` nastaveným na je určena k návratu kontextu do blokovaného stavu tak, aby jej mohl obnovit buď `SwitchTo` nebo `IVirtualProcessorRoot::Activate` v plánovači, od kterého byl odpojen. Vzhledem k tomu, že nebyl spuštěn v kořenovém adresáři virtuálního procesoru, neprobíhá žádná reinicializace.

Reinicializovaný kořen virtuálního procesoru se neliší od zcela nového kořene virtuálního procesoru, který vašemu plánovači udělil Správce prostředků. Můžete jej použít pro spuštění aktivací s `IVirtualProcessorRoot::Activate`kontextem spuštění pomocí .

`SwitchOut`musí být volána na `IThreadProxy` rozhraní, které představuje aktuálně spuštěné vlákno nebo výsledky nejsou definovány.

V knihovnách a záhlavích dodaných se souborem Visual Studio 2010 tato metoda nepřijala parametr a neinicializovala kořenový adresář virtuálního procesoru. Chcete-li zachovat staré chování, `Blocking` je zadána výchozí hodnota parametru.

## <a name="ithreadproxyswitchto-method"></a><a name="switchto"></a>iThreadProxy::Metoda SwitchTo

Provede kooperativní přepnutí kontextu z aktuálně spuštěného kontextu do jiného kontextu.

```cpp
virtual void SwitchTo(
    _Inout_ IExecutionContext* pContext,
    SwitchingProxyState switchState) = 0;
```

### <a name="parameters"></a>Parametry

*pKontext*<br/>
Kontext provádění kooperativně přepnout.

*switchState*<br/>
Označuje stav proxy vlákna, který provádí přepínač. Parametr je typu `SwitchingProxyState`.

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete přepnout z jednoho kontextu spuštění do jiného, z metody [IExecutionContext::Dispatch](iexecutioncontext-structure.md#dispatch) prvního kontextu spuštění. Metoda přidruží `pContext` kontext spuštění k proxy vlákna, pokud již není přidružena k jednomu. Vlastnictví aktuálního proxy vlákna je určeno hodnotou, kterou zadáte pro `switchState` argument.

Hodnotu `Idle` použijte, pokud chcete vrátit aktuálně spuštěný proxy podproces správci prostředků. Volání `SwitchTo` s `switchState` parametrem `Idle` nastaveným na `pContext` způsobí spuštění kontextu spuštění provádění na základní prostředek spuštění. Vlastnictví tohoto proxy podprocesu je převedena do Správce prostředků a očekává `Dispatch` se, `SwitchTo` že vrátí z metody kontextu spuštění brzy po vrátí, za účelem dokončení převodu. Kontext spuštění, který byl odesílán proxy vlákna je odpojen od proxy vlákna a plánovač je zdarma k jeho opětovnému použití nebo zničit, jak uzná za vhodné.

Hodnotu `Blocking` použijte, pokud chcete, aby tento proxy server podprocesu zaujíměl blokovaný stav. Volání `SwitchTo` s `switchState` parametrem `Blocking` nastaveným na `pContext` způsobí spuštění kontextu spuštění a blokovat aktuální proxy vlákna, dokud nebude obnovena. Plánovač si zachová vlastnictví proxy vlákna, když `Blocking` je proxy vlákno ve stavu. Blokující proxy podproces lze obnovit `SwitchTo` voláním funkce přepnout do kontextu spuštění tohoto vlákna proxy. Můžete také obnovit proxy vlákna pomocí jeho přidruženého kontextu k aktivaci kořenového adresáře virtuálního procesoru. Další informace o tom, jak to provést, naleznete v [tématu IVirtualProcessorRoot::Activate](ivirtualprocessorroot-structure.md#activate).

Hodnotu `Nesting` použijte, pokud chcete dočasně odpojit tento proxy podproces od kořene virtuálního procesoru, ve kterém je spuštěn, a plánovač, pro který odesílá práci. Volání `SwitchTo` s `switchState` parametrem `Nesting` nastaveným na `pContext` způsobí spuštění kontextu spuštění a aktuální proxy podproces také pokračuje v provádění bez nutnosti kořenového virtuálního procesoru. Proxy podprocesu je považován za opustil plánovač, dokud volá [IThreadProxy::SwitchOut](#switchout) metoda později v čase. Metoda `IThreadProxy::SwitchOut` může blokovat proxy vlákna, dokud kořenový virtuální procesor je k dispozici pro přeplánování.

`SwitchTo`musí být volána na `IThreadProxy` rozhraní, které představuje aktuálně spuštěné vlákno nebo výsledky nejsou definovány. Funkce `invalid_argument` vyvolá, pokud `pContext` je parametr `NULL`nastaven na .

## <a name="ithreadproxyyieldtosystem-method"></a><a name="yieldtosystem"></a>iThreadProxy::Metoda YieldToSystem

Způsobí, že volající vlákno výnos spuštění do jiného vlákna, který je připraven ke spuštění na aktuální procesor. Operační systém vybere další vlákno, které má být provedeno.

```cpp
virtual void YieldToSystem() = 0;
```

### <a name="remarks"></a>Poznámky

Při volání proxy vlákna podporované ho regulérní podproces `YieldToSystem` `SwitchToThread`windows, se chová přesně jako funkce systému Windows . Však při volání z uživatelského režimu schedulable (UMS) vlákna, `SwitchToThread` funkce deleguje úlohu výběru další vlákno spustit do plánovače uživatelského režimu, nikoli operační systém. Chcete-li dosáhnout požadovaného účinku přepnutí na jiný `YieldToSystem`připravený závit v systému, použijte .

`YieldToSystem`musí být volána na `IThreadProxy` rozhraní, které představuje aktuálně spuštěné vlákno nebo výsledky nejsou definovány.

## <a name="see-also"></a>Viz také

[obor názvů souběžnosti](concurrency-namespace.md)<br/>
[IExecutionContext – struktura](iexecutioncontext-structure.md)<br/>
[IScheduler – struktura](ischeduler-structure.md)<br/>
[IVirtualProcessorRoot – struktura](ivirtualprocessorroot-structure.md)

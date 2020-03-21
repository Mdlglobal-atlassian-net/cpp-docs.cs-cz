---
title: AsyncBase – třída
ms.date: 10/08/2018
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase
- async/Microsoft::WRL::AsyncBase::AsyncBase
- async/Microsoft::WRL::AsyncBase::Cancel
- async/Microsoft::WRL::AsyncBase::CheckValidStateForDelegateCall
- async/Microsoft::WRL::AsyncBase::CheckValidStateForResultsCall
- async/Microsoft::WRL::AsyncBase::Close
- async/Microsoft::WRL::AsyncBase::ContinueAsyncOperation
- async/Microsoft::WRL::AsyncBase::CurrentStatus
- async/Microsoft::WRL::AsyncBase::ErrorCode
- async/Microsoft::WRL::AsyncBase::FireCompletion
- async/Microsoft::WRL::AsyncBase::FireProgress
- async/Microsoft::WRL::AsyncBase::get_ErrorCode
- async/Microsoft::WRL::AsyncBase::get_Id
- async/Microsoft::WRL::AsyncBase::get_Status
- async/Microsoft::WRL::AsyncBase::GetOnComplete
- async/Microsoft::WRL::AsyncBase::GetOnProgress
- async/Microsoft::WRL::AsyncBase::OnCancel
- async/Microsoft::WRL::AsyncBase::OnClose
- async/Microsoft::WRL::AsyncBase::OnStart
- async/Microsoft::WRL::AsyncBase::put_Id
- async/Microsoft::WRL::AsyncBase::PutOnComplete
- async/Microsoft::WRL::AsyncBase::PutOnProgress
- async/Microsoft::WRL::AsyncBase::TryTransitionToCompleted
- async/Microsoft::WRL::AsyncBase::TryTransitionToError
helpviewer_keywords:
- Microsoft::WRL::AsyncBase class
- Microsoft::WRL::AsyncBase::AsyncBase, constructor
- Microsoft::WRL::AsyncBase::Cancel method
- Microsoft::WRL::AsyncBase::CheckValidStateForDelegateCall method
- Microsoft::WRL::AsyncBase::CheckValidStateForResultsCall method
- Microsoft::WRL::AsyncBase::Close method
- Microsoft::WRL::AsyncBase::ContinueAsyncOperation method
- Microsoft::WRL::AsyncBase::CurrentStatus method
- Microsoft::WRL::AsyncBase::ErrorCode method
- Microsoft::WRL::AsyncBase::FireCompletion method
- Microsoft::WRL::AsyncBase::FireProgress method
- Microsoft::WRL::AsyncBase::get_ErrorCode method
- Microsoft::WRL::AsyncBase::get_Id method
- Microsoft::WRL::AsyncBase::get_Status method
- Microsoft::WRL::AsyncBase::GetOnComplete method
- Microsoft::WRL::AsyncBase::GetOnProgress method
- Microsoft::WRL::AsyncBase::OnCancel method
- Microsoft::WRL::AsyncBase::OnClose method
- Microsoft::WRL::AsyncBase::OnStart method
- Microsoft::WRL::AsyncBase::put_Id method
- Microsoft::WRL::AsyncBase::PutOnComplete method
- Microsoft::WRL::AsyncBase::PutOnProgress method
- Microsoft::WRL::AsyncBase::TryTransitionToCompleted method
- Microsoft::WRL::AsyncBase::TryTransitionToError method
ms.assetid: 64259b9b-f427-4ffd-a611-e7a2f82362b2
ms.openlocfilehash: 09819c9e8dd924581ce8cd67233d273f7e8d62ca
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079899"
---
# <a name="asyncbase-class"></a>AsyncBase – třída

Implementuje prostředí Windows Runtime asynchronní Stavový počítač.

## <a name="syntax"></a>Syntaxe

```cpp
template <
    typename TComplete,
    typename TProgress = Details::Nil,
    AsyncResultType resultType = SingleResult
>
class AsyncBase : public AsyncBase<TComplete, Details::Nil, resultType>;

template <typename TComplete, AsyncResultType resultType>
class AsyncBase<TComplete, Details::Nil, resultType> :
    public Microsoft::WRL::Implements<IAsyncInfo>;
```

### <a name="parameters"></a>Parametry

*TComplete*<br/>
Obslužná rutina události, která je volána po dokončení asynchronní operace.

*TProgress*<br/>
Obslužná rutina události, která je volána, když běžící asynchronní operace hlásí aktuální průběh operace.

*Hodnotu*<br/>
Jedna z hodnot výčtu [AsyncResultType –](asyncresulttype-enumeration.md) . Ve výchozím nastavení `SingleResult`.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Název                               | Popis
---------------------------------- | -------------------------------------------------
[AsyncBase:: AsyncBase](#asyncbase) | Inicializuje instanci třídy `AsyncBase`.

### <a name="public-methods"></a>Veřejné metody

Název                                         | Popis
-------------------------------------------- | -------------------------------------------------------------------------------------
[AsyncBase:: Cancel](#cancel)                 | Zruší asynchronní operaci.
[AsyncBase:: Close](#close)                   | Zavře asynchronní operaci.
[AsyncBase:: FireCompletion –](#firecompletion) | Vyvolá obslužnou rutinu události dokončení nebo obnoví interního delegáta průběhu.
[AsyncBase:: FireProgress –](#fireprogress)     | Vyvolá aktuální obslužnou rutinu události průběhu.
[AsyncBase:: get_ErrorCode](#get-errorcode)   | Načte kód chyby aktuální asynchronní operace.
[AsyncBase:: get_Id](#get-id)                 | Načte popisovač asynchronní operace.
[AsyncBase:: get_Status](#get-status)         | Načte hodnotu, která označuje stav asynchronní operace.
[AsyncBase:: Getoncomplete –](#getoncomplete)   | Zkopíruje adresu aktuální obslužné rutiny události dokončení do zadané proměnné.
[AsyncBase:: Getonprogress –](#getonprogress)   | Zkopíruje adresu aktuální obslužné rutiny události průběhu do zadané proměnné.
[AsyncBase::p ut_Id](#put-id)                 | Nastaví popisovač asynchronní operace.
[AsyncBase::P utOnComplete](#putoncomplete)   | Nastaví adresu obslužné rutiny události dokončení na zadanou hodnotu.
[AsyncBase::P utOnProgress](#putonprogress)   | Nastaví adresu obslužné rutiny události průběhu na určenou hodnotu.

### <a name="protected-methods"></a>Chráněné metody

Název                                                                         | Popis
---------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[AsyncBase:: Checkvalidstatefordelegatecall –](#checkvalidstatefordelegatecall) | Testuje, zda lze vlastnosti delegáta upravit v aktuálním asynchronním stavu.
[AsyncBase:: Checkvalidstateforresultscall –](#checkvalidstateforresultscall)   | Testuje, zda mohou být výsledky asynchronní operace shromažďovány v aktuálním asynchronním stavu.
[AsyncBase:: Continueasyncoperation –](#continueasyncoperation)                 | Určuje, zda má být asynchronní operace pokračovat ve zpracování, nebo by měla být zastavena.
[AsyncBase:: currentStatus –](#currentstatus)                                   | Načte stav aktuální asynchronní operace.
[AsyncBase:: ErrorCode](#errorcode)                                           | Načte kód chyby aktuální asynchronní operace.
[AsyncBase::-Cancel](#oncancel)                                             | Při přepsání v odvozené třídě zruší asynchronní operaci.
[AsyncBase::-Close](#onclose)                                               | Při přepsání v odvozené třídě ukončí asynchronní operaci.
[AsyncBase:: OnStart](#onstart)                                               | Při přepsání v odvozené třídě spustí asynchronní operaci.
[AsyncBase:: Start](#start)                                                   | Spustí asynchronní operaci.
[AsyncBase:: Trytransitiontocompleted –](#trytransitiontocompleted)             | Označuje, zda byla aktuální asynchronní operace dokončena.
[AsyncBase:: Trytransitiontoerror –](#trytransitiontoerror)                     | Určuje, zda může zadaný kód chyby upravovat stav interní chyby.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`AsyncBase`

`AsyncBase`

## <a name="requirements"></a>Požadavky

**Hlavička:** Async. h

**Obor názvů:** Microsoft:: WRL

## <a name="asyncbaseasyncbase"></a><a name="asyncbase"></a>AsyncBase:: AsyncBase

Inicializuje instanci třídy `AsyncBase`.

```cpp
AsyncBase();
```

## <a name="asyncbasecancel"></a><a name="cancel"></a>AsyncBase:: Cancel

Zruší asynchronní operaci.

```cpp
STDMETHOD(
   Cancel
)(void);
```

### <a name="return-value"></a>Návratová hodnota

Ve výchozím nastavení vždy vrátí S_OK.

### <a name="remarks"></a>Poznámky

`Cancel()` je výchozí implementace `IAsyncInfo::Cancel`a nemá žádnou skutečnou práci. Chcete-li skutečně zrušit asynchronní operaci, přepište `OnCancel()` čistě virtuální metodu.

## <a name="asyncbasecheckvalidstatefordelegatecall"></a><a name="checkvalidstatefordelegatecall"></a>AsyncBase:: Checkvalidstatefordelegatecall –

Testuje, zda lze vlastnosti delegáta upravit v aktuálním asynchronním stavu.

```cpp
inline HRESULT CheckValidStateForDelegateCall();
```

### <a name="return-value"></a>Návratová hodnota

S_OK, pokud lze změnit vlastnosti delegáta; v opačném případě E_ILLEGAL_METHOD_CALL.

## <a name="asyncbasecheckvalidstateforresultscall"></a><a name="checkvalidstateforresultscall"></a>AsyncBase:: Checkvalidstateforresultscall –

Testuje, zda mohou být výsledky asynchronní operace shromažďovány v aktuálním asynchronním stavu.

```cpp
inline HRESULT CheckValidStateForResultsCall();
```

### <a name="return-value"></a>Návratová hodnota

S_OK, pokud se mají shromažďovat výsledky; v opačném případě E_ILLEGAL_METHOD_CALLE_ILLEGAL_METHOD_CALL.

## <a name="asyncbaseclose"></a><a name="close"></a>AsyncBase:: Close

Zavře asynchronní operaci.

```cpp
STDMETHOD(
   Close
)(void) override;
```

### <a name="return-value"></a>Návratová hodnota

S_OK, zda je operace ukončena nebo je již zavřena; v opačném případě E_ILLEGAL_STATE_CHANGE.

### <a name="remarks"></a>Poznámky

`Close()` je výchozí implementace `IAsyncInfo::Close`a nemá žádnou skutečnou práci. Chcete-li skutečně ukončit asynchronní operaci, přepište `OnClose()` čistě virtuální metodu.

## <a name="asyncbasecontinueasyncoperation"></a><a name="continueasyncoperation"></a>AsyncBase:: Continueasyncoperation –

Určuje, zda má být asynchronní operace pokračovat ve zpracování, nebo by měla být zastavena.

```cpp
inline bool ContinueAsyncOperation();
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je aktuální stav asynchronní operace *spuštěno*, což znamená, že operace by měla pokračovat. V opačném případě **false**, což znamená, že operace by se měla zastavit.

## <a name="asyncbasecurrentstatus"></a><a name="currentstatus"></a>AsyncBase:: currentStatus –

Načte stav aktuální asynchronní operace.

```cpp
inline void CurrentStatus(
   Details::AsyncStatusInternal *status
);
```

### <a name="parameters"></a>Parametry

*stav*<br/>
Umístění, kde tato operace ukládá aktuální stav.

### <a name="remarks"></a>Poznámky

Tato operace je bezpečná pro přístup z více vláken.

## <a name="asyncbaseerrorcode"></a><a name="errorcode"></a>AsyncBase:: ErrorCode

Načte kód chyby aktuální asynchronní operace.

```cpp
inline void ErrorCode(
   HRESULT *error
);
```

### <a name="parameters"></a>Parametry

*Chyba*<br/>
Umístění, kde tato operace ukládá aktuální kód chyby.

### <a name="remarks"></a>Poznámky

Tato operace je bezpečná pro přístup z více vláken.

## <a name="asyncbasefirecompletion"></a><a name="firecompletion"></a>AsyncBase:: FireCompletion –

Vyvolá obslužnou rutinu události dokončení nebo obnoví interního delegáta průběhu.

```cpp
void FireCompletion(
   void
) override;

virtual void FireCompletion();
```

### <a name="remarks"></a>Poznámky

První verze `FireCompletion()` obnoví proměnnou delegáta interního průběhu. Druhá verze vyvolá obslužnou rutinu události dokončení, pokud je asynchronní operace dokončena.

## <a name="asyncbasefireprogress"></a><a name="fireprogress"></a>AsyncBase:: FireProgress –

Vyvolá aktuální obslužnou rutinu události průběhu.

```cpp
void FireProgress(
   const typename ProgressTraits::Arg2Type arg
);
```

### <a name="parameters"></a>Parametry

*ARG*<br/>
Metoda obslužné rutiny události, která se má vyvolat

### <a name="remarks"></a>Poznámky

`ProgressTraits` je odvozen ze [struktury ArgTraitsHelper –](argtraitshelper-structure.md).

## <a name="asyncbaseget_errorcode"></a><a name="get-errorcode"></a>AsyncBase:: get_ErrorCode

Načte kód chyby aktuální asynchronní operace.

```cpp
STDMETHOD(
   get_ErrorCode
)(HRESULT* errorCode) override;
```

### <a name="parameters"></a>Parametry

*errorCode*<br/>
Umístění, kde je uložen aktuální kód chyby.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak E_ILLEGAL_METHOD_CALL, pokud je aktuální asynchronní operace zavřena.

## <a name="asyncbaseget_id"></a><a name="get-id"></a>AsyncBase:: get_Id

Načte popisovač asynchronní operace.

```cpp
STDMETHOD(
   get_Id
)(unsigned int *id) override;
```

### <a name="parameters"></a>Parametry

*id*<br/>
Umístění, kam má být popisovač uložen.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě E_ILLEGAL_METHOD_CALL.

### <a name="remarks"></a>Poznámky

Tato metoda implementuje `IAsyncInfo::get_Id`.

## <a name="asyncbaseget_status"></a><a name="get-status"></a>AsyncBase:: get_Status

Načte hodnotu, která označuje stav asynchronní operace.

```cpp
STDMETHOD(
   get_Status
)(AsyncStatus *status) override;
```

### <a name="parameters"></a>Parametry

*stav*<br/>
Umístění, kde má být stav uložen. Další informace najdete v tématu výčet `Windows::Foundation::AsyncStatus`.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě E_ILLEGAL_METHOD_CALL.

### <a name="remarks"></a>Poznámky

Tato metoda implementuje `IAsyncInfo::get_Status`.

## <a name="asyncbasegetoncomplete"></a><a name="getoncomplete"></a>AsyncBase:: Getoncomplete –

Zkopíruje adresu aktuální obslužné rutiny události dokončení do zadané proměnné.

```cpp
STDMETHOD(
   GetOnComplete
)(TComplete** completeHandler);
```

### <a name="parameters"></a>Parametry

*completeHandler*<br/>
Umístění, kde je uložena adresa obslužné rutiny události aktuálního dokončení.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě E_ILLEGAL_METHOD_CALL.

## <a name="asyncbasegetonprogress"></a><a name="getonprogress"></a>AsyncBase:: Getonprogress –

Zkopíruje adresu aktuální obslužné rutiny události průběhu do zadané proměnné.

```cpp
STDMETHOD(
   GetOnProgress
)(TProgress** progressHandler);
```

### <a name="parameters"></a>Parametry

*progressHandler*<br/>
Umístění, kde je uložena adresa obslužné rutiny události aktuálního průběhu.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě E_ILLEGAL_METHOD_CALL.

## <a name="asyncbaseoncancel"></a><a name="oncancel"></a>AsyncBase::-Cancel

Při přepsání v odvozené třídě zruší asynchronní operaci.

```cpp
virtual void OnCancel(
   void
) = 0;
```

## <a name="asyncbaseonclose"></a><a name="onclose"></a>AsyncBase::-Close

Při přepsání v odvozené třídě ukončí asynchronní operaci.

```cpp
virtual void OnClose(
   void
) = 0;
```

## <a name="asyncbaseonstart"></a><a name="onstart"></a>AsyncBase:: OnStart

Při přepsání v odvozené třídě spustí asynchronní operaci.

```cpp
virtual HRESULT OnStart(
   void
) = 0;
```

## <a name="asyncbaseput_id"></a><a name="put-id"></a>AsyncBase::p ut_Id

Nastaví popisovač asynchronní operace.

```cpp
STDMETHOD(
   put_Id
)(const unsigned int id);
```

### <a name="parameters"></a>Parametry

*id*<br/>
Nenulový popisovač.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě E_INVALIDARG nebo E_ILLEGAL_METHOD_CALL.

## <a name="asyncbaseputoncomplete"></a><a name="putoncomplete"></a>AsyncBase::P utOnComplete

Nastaví adresu obslužné rutiny události dokončení na zadanou hodnotu.

```cpp
STDMETHOD(
   PutOnComplete
)(TComplete* completeHandler);
```

### <a name="parameters"></a>Parametry

*completeHandler*<br/>
Adresa, na kterou je nastavena obslužná rutina události dokončení

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě E_ILLEGAL_METHOD_CALL.

## <a name="asyncbaseputonprogress"></a><a name="putonprogress"></a>AsyncBase::P utOnProgress

Nastaví adresu obslužné rutiny události průběhu na určenou hodnotu.

```cpp
STDMETHOD(
   PutOnProgress
)(TProgress* progressHandler);
```

### <a name="parameters"></a>Parametry

*progressHandler*<br/>
Adresa, na kterou je obslužná rutina události průběhu nastavena.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě E_ILLEGAL_METHOD_CALL.

## <a name="asyncbasestart"></a><a name="start"></a>AsyncBase:: Start

Spustí asynchronní operaci.

```cpp
STDMETHOD(
   Start
)(void);
```

### <a name="return-value"></a>Návratová hodnota

S_OK, zda je operace spuštěna nebo je již spuštěna; v opačném případě E_ILLEGAL_STATE_CHANGE.

### <a name="remarks"></a>Poznámky

`Start()` je chráněná metoda, která není externě viditelná, protože před návratem k volajícímu se musí spustit asynchronní operace "Hot Start".

## <a name="asyncbasetrytransitiontocompleted"></a><a name="trytransitiontocompleted"></a>AsyncBase:: Trytransitiontocompleted –

Označuje, zda byla aktuální asynchronní operace dokončena.

```cpp
bool TryTransitionToCompleted(
   void
);
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud se asynchronní operace dokončila; v opačném případě **false**.

## <a name="asyncbasetrytransitiontoerror"></a><a name="trytransitiontoerror"></a>AsyncBase:: Trytransitiontoerror –

Určuje, zda může zadaný kód chyby upravovat stav interní chyby.

```cpp
bool TryTransitionToError(
   const HRESULT error
);
```

### <a name="parameters"></a>Parametry

*Chyba*<br/>
Chyba HRESULT.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud došlo ke změně stavu vnitřní chyby; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Tato operace upraví chybový stav pouze v případě, že stav chyby je již nastaven na S_OK. Tato operace nemá žádný vliv, pokud chybový stav je již chyba, zrušeno, dokončeno nebo Uzavřeno.

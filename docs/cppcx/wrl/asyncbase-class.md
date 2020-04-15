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
ms.openlocfilehash: 0254aa4dc243eeffa43850c437a833a6530c01e2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371864"
---
# <a name="asyncbase-class"></a>AsyncBase – třída

Implementuje asynchronní stavový počítač prostředí prostředí prostředí Prostředí Prostředí Spustit za prostředí systému Windows Runtime.

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

*TKompletní*<br/>
Obslužná rutina události, která je volána po dokončení asynchronní operace.

*TProgress*<br/>
Obslužná rutina události, která je volána při spuštění asynchronní operace hlásí aktuální průběh operace.

*resultType*<br/>
Jedna z hodnot výčtu [AsyncResultType.](asyncresulttype-enumeration.md) Ve výchozím `SingleResult`nastavení .

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Name (Název)                               | Popis
---------------------------------- | -------------------------------------------------
[AsyncBase::AsyncBase](#asyncbase) | Inicializuje instanci třídy `AsyncBase`.

### <a name="public-methods"></a>Veřejné metody

Name (Název)                                         | Popis
-------------------------------------------- | -------------------------------------------------------------------------------------
[AsyncBase::Zrušit](#cancel)                 | Zruší asynchronní operaci.
[AsyncBase::Zavřít](#close)                   | Zavře asynchronní operaci.
[AsyncBase::Dokončení požáru](#firecompletion) | Vyvolá obslužnou rutinu události dokončení nebo obnoví interní delegáta průběhu.
[AsyncBase::FireProgress](#fireprogress)     | Vyvolá aktuální obslužnou rutinu události průběhu.
[AsyncBase::get_ErrorCode](#get-errorcode)   | Načte kód chyby pro aktuální asynchronní operaci.
[AsyncBase::get_Id](#get-id)                 | Načte popisovač asynchronní operace.
[AsyncBase::get_Status](#get-status)         | Načte hodnotu, která označuje stav asynchronní operace.
[AsyncBase::GetOnComplete](#getoncomplete)   | Zkopíruje adresu aktuální obslužné rutiny události dokončení na zadanou proměnnou.
[AsyncBase::GetOnProgress](#getonprogress)   | Zkopíruje adresu aktuální obslužné rutiny události průběhu na zadanou proměnnou.
[AsyncBase::put_Id](#put-id)                 | Nastaví popisovač asynchronní operace.
[AsyncBase::PutOnComplete](#putoncomplete)   | Nastaví adresu obslužné rutiny události dokončení na zadanou hodnotu.
[AsyncBase::PutOnProgress](#putonprogress)   | Nastaví adresu obslužné rutiny události průběhu na zadanou hodnotu.

### <a name="protected-methods"></a>Chráněné metody

Name (Název)                                                                         | Popis
---------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[AsyncBase::CheckValidStateForDelegateCall](#checkvalidstatefordelegatecall) | Testuje, zda lze vlastnosti delegáta změnit v aktuálním asynchronním stavu.
[AsyncBase::CheckValidStateForResultsCall](#checkvalidstateforresultscall)   | Testuje, zda výsledky asynchronní operace mohou být shromažďovány v aktuálním asynchronním stavu.
[AsyncBase::ContinueAsyncOperation](#continueasyncoperation)                 | Určuje, zda asynchronní operace by měla pokračovat ve zpracování nebo by měla být zastavena.
[AsyncBase::CurrentStatus](#currentstatus)                                   | Načte stav aktuální asynchronní operace.
[AsyncBase::ErrorCode](#errorcode)                                           | Načte kód chyby pro aktuální asynchronní operaci.
[AsyncBase::OnCancel](#oncancel)                                             | Při přepsání v odvozené třídě zruší asynchronní operaci.
[AsyncBase::OnClose](#onclose)                                               | Při přepsání v odvozené třídě zavře asynchronní operaci.
[AsyncBase::Při spuštění](#onstart)                                               | Při přepsání v odvozené třídě spustí asynchronní operaci.
[AsyncBase::Start](#start)                                                   | Spustí asynchronní operaci.
[AsyncBase::TryTransitionToCompleted](#trytransitiontocompleted)             | Označuje, zda byla dokončena aktuální asynchronní operace.
[Asynchronní základna::TryTransitionToError](#trytransitiontoerror)                     | Označuje, zda zadaný kód chyby může změnit stav vnitřní chyby.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`AsyncBase`

`AsyncBase`

## <a name="requirements"></a>Požadavky

**Záhlaví:** async.h

**Obor názvů:** Microsoft::WRL

## <a name="asyncbaseasyncbase"></a><a name="asyncbase"></a>AsyncBase::AsyncBase

Inicializuje instanci třídy `AsyncBase`.

```cpp
AsyncBase();
```

## <a name="asyncbasecancel"></a><a name="cancel"></a>AsyncBase::Zrušit

Zruší asynchronní operaci.

```cpp
STDMETHOD(
   Cancel
)(void);
```

### <a name="return-value"></a>Návratová hodnota

Ve výchozím nastavení vždy vrátí S_OK.

### <a name="remarks"></a>Poznámky

`Cancel()`je výchozí implementace `IAsyncInfo::Cancel`aplikace , a neprovádí žádnou skutečnou práci. Chcete-li skutečně zrušit asynchronní operaci, přepište `OnCancel()` čistě virtuální metodu.

## <a name="asyncbasecheckvalidstatefordelegatecall"></a><a name="checkvalidstatefordelegatecall"></a>AsyncBase::CheckValidStateForDelegateCall

Testuje, zda lze vlastnosti delegáta změnit v aktuálním asynchronním stavu.

```cpp
inline HRESULT CheckValidStateForDelegateCall();
```

### <a name="return-value"></a>Návratová hodnota

S_OK, pokud lze změnit vlastnosti delegáta; jinak E_ILLEGAL_METHOD_CALL.

## <a name="asyncbasecheckvalidstateforresultscall"></a><a name="checkvalidstateforresultscall"></a>AsyncBase::CheckValidStateForResultsCall

Testuje, zda výsledky asynchronní operace mohou být shromažďovány v aktuálním asynchronním stavu.

```cpp
inline HRESULT CheckValidStateForResultsCall();
```

### <a name="return-value"></a>Návratová hodnota

S_OK, pokud lze shromažďovat výsledky; jinak E_ILLEGAL_METHOD_CALLE_ILLEGAL_METHOD_CALL.

## <a name="asyncbaseclose"></a><a name="close"></a>AsyncBase::Zavřít

Zavře asynchronní operaci.

```cpp
STDMETHOD(
   Close
)(void) override;
```

### <a name="return-value"></a>Návratová hodnota

S_OK, pokud se operace uzavře nebo je již uzavřena; jinak E_ILLEGAL_STATE_CHANGE.

### <a name="remarks"></a>Poznámky

`Close()`je výchozí implementace `IAsyncInfo::Close`aplikace , a neprovádí žádnou skutečnou práci. Chcete-li skutečně zavřít asynchronní operaci, přepsat `OnClose()` čistě virtuální metodu.

## <a name="asyncbasecontinueasyncoperation"></a><a name="continueasyncoperation"></a>AsyncBase::ContinueAsyncOperation

Určuje, zda asynchronní operace by měla pokračovat ve zpracování nebo by měla být zastavena.

```cpp
inline bool ContinueAsyncOperation();
```

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je *spuštěn*aktuální stav asynchronní operace , což znamená, že operace by měla pokračovat. V opačném případě **false**, což znamená, že operace by měla zastavit.

## <a name="asyncbasecurrentstatus"></a><a name="currentstatus"></a>AsyncBase::CurrentStatus

Načte stav aktuální asynchronní operace.

```cpp
inline void CurrentStatus(
   Details::AsyncStatusInternal *status
);
```

### <a name="parameters"></a>Parametry

*Stav*<br/>
Umístění, kde tato operace ukládá aktuální stav.

### <a name="remarks"></a>Poznámky

Tato operace je bezpečná pro přístup z více vláken.

## <a name="asyncbaseerrorcode"></a><a name="errorcode"></a>AsyncBase::ErrorCode

Načte kód chyby pro aktuální asynchronní operaci.

```cpp
inline void ErrorCode(
   HRESULT *error
);
```

### <a name="parameters"></a>Parametry

*error*<br/>
Umístění, kde tato operace ukládá aktuální kód chyby.

### <a name="remarks"></a>Poznámky

Tato operace je bezpečná pro přístup z více vláken.

## <a name="asyncbasefirecompletion"></a><a name="firecompletion"></a>AsyncBase::Dokončení požáru

Vyvolá obslužnou rutinu události dokončení nebo obnoví interní delegáta průběhu.

```cpp
void FireCompletion(
   void
) override;

virtual void FireCompletion();
```

### <a name="remarks"></a>Poznámky

První verze `FireCompletion()` obnoví interní průběh delegátproměnné. Druhá verze vyvolá obslužnou rutinu události dokončení, pokud je asynchronní operace dokončena.

## <a name="asyncbasefireprogress"></a><a name="fireprogress"></a>AsyncBase::FireProgress

Vyvolá aktuální obslužnou rutinu události průběhu.

```cpp
void FireProgress(
   const typename ProgressTraits::Arg2Type arg
);
```

### <a name="parameters"></a>Parametry

*Arg*<br/>
Metoda obslužné rutiny události, která má být vyvolána.

### <a name="remarks"></a>Poznámky

`ProgressTraits`je odvozen a [argtraitsHelper struktura](argtraitshelper-structure.md).

## <a name="asyncbaseget_errorcode"></a><a name="get-errorcode"></a>AsyncBase::get_ErrorCode

Načte kód chyby pro aktuální asynchronní operaci.

```cpp
STDMETHOD(
   get_ErrorCode
)(HRESULT* errorCode) override;
```

### <a name="parameters"></a>Parametry

*Errorcode*<br/>
Umístění, kde je uložen aktuální kód chyby.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě E_ILLEGAL_METHOD_CALL, pokud je aktuální asynchronní operace uzavřena.

## <a name="asyncbaseget_id"></a><a name="get-id"></a>AsyncBase::get_Id

Načte popisovač asynchronní operace.

```cpp
STDMETHOD(
   get_Id
)(unsigned int *id) override;
```

### <a name="parameters"></a>Parametry

*Id*<br/>
Umístění, kde má být popisovač uložen.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak E_ILLEGAL_METHOD_CALL.

### <a name="remarks"></a>Poznámky

Tato metoda `IAsyncInfo::get_Id`implementuje .

## <a name="asyncbaseget_status"></a><a name="get-status"></a>AsyncBase::get_Status

Načte hodnotu, která označuje stav asynchronní operace.

```cpp
STDMETHOD(
   get_Status
)(AsyncStatus *status) override;
```

### <a name="parameters"></a>Parametry

*Stav*<br/>
Umístění, kde má být stav uložen. Další informace naleznete `Windows::Foundation::AsyncStatus` v tématu výčet.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak E_ILLEGAL_METHOD_CALL.

### <a name="remarks"></a>Poznámky

Tato metoda `IAsyncInfo::get_Status`implementuje .

## <a name="asyncbasegetoncomplete"></a><a name="getoncomplete"></a>AsyncBase::GetOnComplete

Zkopíruje adresu aktuální obslužné rutiny události dokončení na zadanou proměnnou.

```cpp
STDMETHOD(
   GetOnComplete
)(TComplete** completeHandler);
```

### <a name="parameters"></a>Parametry

*completeHandler*<br/>
Umístění, kde je uložena adresa aktuální obslužné rutiny události dokončení.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak E_ILLEGAL_METHOD_CALL.

## <a name="asyncbasegetonprogress"></a><a name="getonprogress"></a>AsyncBase::GetOnProgress

Zkopíruje adresu aktuální obslužné rutiny události průběhu na zadanou proměnnou.

```cpp
STDMETHOD(
   GetOnProgress
)(TProgress** progressHandler);
```

### <a name="parameters"></a>Parametry

*progressHandler*<br/>
Umístění, kde je uložena adresa aktuální obslužné rutiny události průběhu.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak E_ILLEGAL_METHOD_CALL.

## <a name="asyncbaseoncancel"></a><a name="oncancel"></a>AsyncBase::OnCancel

Při přepsání v odvozené třídě zruší asynchronní operaci.

```cpp
virtual void OnCancel(
   void
) = 0;
```

## <a name="asyncbaseonclose"></a><a name="onclose"></a>AsyncBase::OnClose

Při přepsání v odvozené třídě zavře asynchronní operaci.

```cpp
virtual void OnClose(
   void
) = 0;
```

## <a name="asyncbaseonstart"></a><a name="onstart"></a>AsyncBase::Při spuštění

Při přepsání v odvozené třídě spustí asynchronní operaci.

```cpp
virtual HRESULT OnStart(
   void
) = 0;
```

## <a name="asyncbaseput_id"></a><a name="put-id"></a>AsyncBase::put_Id

Nastaví popisovač asynchronní operace.

```cpp
STDMETHOD(
   put_Id
)(const unsigned int id);
```

### <a name="parameters"></a>Parametry

*Id*<br/>
Nenulový popisovač.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě E_INVALIDARG nebo E_ILLEGAL_METHOD_CALL.

## <a name="asyncbaseputoncomplete"></a><a name="putoncomplete"></a>AsyncBase::PutOnComplete

Nastaví adresu obslužné rutiny události dokončení na zadanou hodnotu.

```cpp
STDMETHOD(
   PutOnComplete
)(TComplete* completeHandler);
```

### <a name="parameters"></a>Parametry

*completeHandler*<br/>
Adresa, na kterou je nastavena obslužná rutina události dokončení.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak E_ILLEGAL_METHOD_CALL.

## <a name="asyncbaseputonprogress"></a><a name="putonprogress"></a>AsyncBase::PutOnProgress

Nastaví adresu obslužné rutiny události průběhu na zadanou hodnotu.

```cpp
STDMETHOD(
   PutOnProgress
)(TProgress* progressHandler);
```

### <a name="parameters"></a>Parametry

*progressHandler*<br/>
Adresa, na kterou je nastavena obslužná rutina události průběhu.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak E_ILLEGAL_METHOD_CALL.

## <a name="asyncbasestart"></a><a name="start"></a>AsyncBase::Start

Spustí asynchronní operaci.

```cpp
STDMETHOD(
   Start
)(void);
```

### <a name="return-value"></a>Návratová hodnota

S_OK pokud je operace spuštěna nebo již spuštěna. jinak E_ILLEGAL_STATE_CHANGE.

### <a name="remarks"></a>Poznámky

`Start()`je chráněná metoda, která není externě viditelná, protože asynchronní operace "hot start" před návratem volajícímu.

## <a name="asyncbasetrytransitiontocompleted"></a><a name="trytransitiontocompleted"></a>AsyncBase::TryTransitionToCompleted

Označuje, zda byla dokončena aktuální asynchronní operace.

```cpp
bool TryTransitionToCompleted(
   void
);
```

### <a name="return-value"></a>Návratová hodnota

**true,** pokud byla dokončena asynchronní operace; jinak **false**.

## <a name="asyncbasetrytransitiontoerror"></a><a name="trytransitiontoerror"></a>Asynchronní základna::TryTransitionToError

Označuje, zda zadaný kód chyby může změnit stav vnitřní chyby.

```cpp
bool TryTransitionToError(
   const HRESULT error
);
```

### <a name="parameters"></a>Parametry

*error*<br/>
Chyba HRESULT.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud byl změněn stav vnitřní chyby; jinak **false**.

### <a name="remarks"></a>Poznámky

Tato operace upraví chybový stav pouze v případě, že je stav chyby již nastaven na S_OK. Tato operace nemá žádný vliv, pokud je chybový stav již chybový, zrušený, dokončený nebo uzavřený.

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
ms.openlocfilehash: 367d0b0cd3197623b27ee1a50e804cca797aedf3
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334716"
---
# <a name="asyncbase-class"></a>AsyncBase – třída

Implementuje asynchronní stav počítače Windows Runtime.

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
Obslužná rutina události, která je volána při spuštěné asynchronní operace nahlásí aktuální průběh operace.

*resultType*<br/>
Jeden z [asyncresulttype –](asyncresulttype-enumeration.md) hodnot výčtu. Ve výchozím nastavení `SingleResult`.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Název                               | Popis
---------------------------------- | -------------------------------------------------
[Asyncbase::asyncbase –](#asyncbase) | Inicializuje novou instanci `AsyncBase` třídy.

### <a name="public-methods"></a>Veřejné metody

Název                                         | Popis
-------------------------------------------- | -------------------------------------------------------------------------------------
[Asyncbase::Cancel –](#cancel)                 | Zruší asynchronní operace.
[Asyncbase::Close –](#close)                   | Ukončí asynchronní operaci.
[Asyncbase::firecompletion –](#firecompletion) | Vyvolá obslužnou rutinu události dokončení nebo obnoví vnitřní průběh delegáta.
[Asyncbase::fireprogress –](#fireprogress)     | Vyvolá obslužnou rutinu události aktuální průběh.
[AsyncBase::get_ErrorCode](#get-errorcode)   | Získá kód chyby pro aktuální asynchronní operaci.
[AsyncBase::get_Id](#get-id)                 | Načte popisovač asynchronní operace.
[AsyncBase::get_Status](#get-status)         | Načte hodnotu označující stav asynchronní operace.
[Asyncbase::getoncomplete –](#getoncomplete)   | Adresa aktuálního obslužné rutiny události dokončení zkopíruje do zadané proměnné.
[Asyncbase::getonprogress –](#getonprogress)   | Adresa obslužné rutiny události aktuální průběh zkopíruje do zadané proměnné.
[Asyncbase::put_id –](#put-id)                 | Nastaví popisovač asynchronní operace.
[Asyncbase::putoncomplete –](#putoncomplete)   | Nastaví adresu obslužné rutiny události dokončení se zadanou hodnotou.
[AsyncBase::PutOnProgress](#putonprogress)   | Nastaví adresu průběh obslužné rutiny události se zadanou hodnotou.


### <a name="protected-methods"></a>Chráněné metody

Název                                                                         | Popis
---------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[AsyncBase::CheckValidStateForDelegateCall](#checkvalidstatefordelegatecall) | Ověřuje, zda vlastnosti delegáta lze upravit v aktuálním asynchronní stavu.
[AsyncBase::CheckValidStateForResultsCall](#checkvalidstateforresultscall)   | Testuje, jestli výsledky asynchronní operace se můžou shromažďovat v aktuálním asynchronní stavu.
[AsyncBase::ContinueAsyncOperation](#continueasyncoperation)                 | Určuje, zda by měly pokračovat ve zpracování asynchronní operaci, nebo by měla zastavit.
[Asyncbase::currentStatus –](#currentstatus)                                   | Načte stav aktuální asynchronní operace.
[AsyncBase::ErrorCode](#errorcode)                                           | Získá kód chyby pro aktuální asynchronní operaci.
[Asyncbase::oncancel –](#oncancel)                                             | Při přepisu v odvozené třídě, zruší asynchronní operace.
[Asyncbase::onclose –](#onclose)                                               | Při přepisu v odvozené třídě, ukončí asynchronní operaci.
[AsyncBase::OnStart](#onstart)                                               | Při přepisu v odvozené třídě, spustí asynchronní operaci.
[Asyncbase::Start –](#start)                                                   | Spustí asynchronní operaci.
[Asyncbase::trytransitiontocompleted –](#trytransitiontocompleted)             | Určuje, zda aktuální asynchronní operace byla dokončena.
[Asyncbase::trytransitiontoerror –](#trytransitiontoerror)                     | Určuje, zda kód zadanou chybovou můžete upravit stavu došlo k vnitřní chybě.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`AsyncBase`

`AsyncBase`

## <a name="requirements"></a>Požadavky

**Záhlaví:** async.h

**Namespace:** Microsoft::WRL

## <a name="asyncbase"></a>Asyncbase::asyncbase –

Inicializuje novou instanci `AsyncBase` třídy.

```cpp
AsyncBase();
```

## <a name="cancel"></a>Asyncbase::Cancel –

Zruší asynchronní operace.

```cpp
STDMETHOD(
   Cancel
)(void);
```

### <a name="return-value"></a>Návratová hodnota

Ve výchozím nastavení vždy vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

`Cancel()` je výchozí implementace `IAsyncInfo::Cancel`, a nemá žádné samotnou práci. Pokud chcete skutečně zrušit asynchronní operaci, přepsat `OnCancel()` čistě virtuální metody.

## <a name="checkvalidstatefordelegatecall"></a>AsyncBase::CheckValidStateForDelegateCall

Ověřuje, zda vlastnosti delegáta lze upravit v aktuálním asynchronní stavu.

```cpp
inline HRESULT CheckValidStateForDelegateCall();
```

### <a name="return-value"></a>Návratová hodnota

S_OK, pokud lze upravovat vlastnosti delegáta. v opačném případě E_ILLEGAL_METHOD_CALL.

## <a name="checkvalidstateforresultscall"></a>AsyncBase::CheckValidStateForResultsCall

Testuje, jestli výsledky asynchronní operace se můžou shromažďovat v aktuálním asynchronní stavu.

```cpp
inline HRESULT CheckValidStateForResultsCall();
```

### <a name="return-value"></a>Návratová hodnota

Pokud výsledky se můžou shromažďovat; S_OK v opačném případě E_ILLEGAL_METHOD_CALLE_ILLEGAL_METHOD_CALL.

## <a name="close"></a>Asyncbase::Close –

Ukončí asynchronní operaci.

```cpp
STDMETHOD(
   Close
)(void) override;
```

### <a name="return-value"></a>Návratová hodnota

S_OK Pokud operace ukončí nebo je již uzavřeno; v opačném případě E_ILLEGAL_STATE_CHANGE.

### <a name="remarks"></a>Poznámky

`Close()` je výchozí implementace `IAsyncInfo::Close`, a nemá žádné samotnou práci. Ve skutečnosti zavřete asynchronní operace, přepsat `OnClose()` čistě virtuální metody.

## <a name="continueasyncoperation"></a>AsyncBase::ContinueAsyncOperation

Určuje, zda by měly pokračovat ve zpracování asynchronní operaci, nebo by měla zastavit.

```cpp
inline bool ContinueAsyncOperation();
```

### <a name="return-value"></a>Návratová hodnota

**true** -li aktuální stav asynchronní operace *spuštění*, což znamená, že operace má pokračovat. V opačném případě **false**, což znamená, že operace by měla zastavit.

## <a name="currentstatus"></a>Asyncbase::currentStatus –

Načte stav aktuální asynchronní operace.

```cpp
inline void CurrentStatus(
   Details::AsyncStatusInternal *status
);
```

### <a name="parameters"></a>Parametry

*status*<br/>
Umístění, kde tato operace uloží aktuální stav.

### <a name="remarks"></a>Poznámky

Tato operace je bezpečná pro vlákno.

## <a name="errorcode"></a>Asyncbase::ErrorCode –

Získá kód chyby pro aktuální asynchronní operaci.

```cpp
inline void ErrorCode(
   HRESULT *error
);
```

### <a name="parameters"></a>Parametry

*error*<br/>
Umístění, kde tato operace ukládá aktuální kód chyby.

### <a name="remarks"></a>Poznámky

Tato operace je bezpečná pro vlákno.

## <a name="firecompletion"></a>Asyncbase::firecompletion –

Vyvolá obslužnou rutinu události dokončení nebo obnoví vnitřní průběh delegáta.

```cpp
void FireCompletion(
   void
) override;

virtual void FireCompletion();
```

### <a name="remarks"></a>Poznámky

První verze `FireCompletion()` obnoví vnitřní průběh proměnné delegáta. Druhá verze vyvolá obslužnou rutinu události dokončení pokud asynchronní operace nebude dokončena.

## <a name="fireprogress"></a>Asyncbase::fireprogress –

Vyvolá obslužnou rutinu události aktuální průběh.

```cpp
void FireProgress(
   const typename ProgressTraits::Arg2Type arg
);
```

### <a name="parameters"></a>Parametry

*arg*<br/>
Metoda obslužné rutiny události, která se má vyvolat.

### <a name="remarks"></a>Poznámky

`ProgressTraits` je odvozen z [argtraitshelper – struktura](argtraitshelper-structure.md).

## <a name="get-errorcode"></a>AsyncBase::get_ErrorCode

Získá kód chyby pro aktuální asynchronní operaci.

```cpp
STDMETHOD(
   get_ErrorCode
)(HRESULT* errorCode) override;
```

### <a name="parameters"></a>Parametry

*errorCode*<br/>
Umístění, kde je uložen aktuální kód chyby.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě E_ILLEGAL_METHOD_CALL, pokud se zavře aktuální asynchronní operace.

## <a name="get-id"></a>AsyncBase::get_Id

Načte popisovač asynchronní operace.

```cpp
STDMETHOD(
   get_Id
)(unsigned int *id) override;
```

### <a name="parameters"></a>Parametry

*id*<br/>
Umístění, kam se uloží popisovač.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě E_ILLEGAL_METHOD_CALL.

### <a name="remarks"></a>Poznámky

Tato metoda implementuje `IAsyncInfo::get_Id`.

## <a name="get-status"></a>AsyncBase::get_Status

Načte hodnotu označující stav asynchronní operace.

```cpp
STDMETHOD(
   get_Status
)(AsyncStatus *status) override;
```

### <a name="parameters"></a>Parametry

*status*<br/>
Umístění, kde má být uložen stav. Další informace najdete v tématu `Windows::Foundation::AsyncStatus` výčtu.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě E_ILLEGAL_METHOD_CALL.

### <a name="remarks"></a>Poznámky

Tato metoda implementuje `IAsyncInfo::get_Status`.

## <a name="getoncomplete"></a>Asyncbase::getoncomplete –

Adresa aktuálního obslužné rutiny události dokončení zkopíruje do zadané proměnné.

```cpp
STDMETHOD(
   GetOnComplete
)(TComplete** completeHandler);
```

### <a name="parameters"></a>Parametry

*completeHandler*<br/>
Umístění, kde je uložen adresu aktuální obslužné rutiny události dokončení.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě E_ILLEGAL_METHOD_CALL.

## <a name="getonprogress"></a>Asyncbase::getonprogress –

Adresa obslužné rutiny události aktuální průběh zkopíruje do zadané proměnné.

```cpp
STDMETHOD(
   GetOnProgress
)(TProgress** progressHandler);
```

### <a name="parameters"></a>Parametry

*progressHandler*<br/>
Umístění, kde je uložen adresu obslužné rutiny události aktuální průběh.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě E_ILLEGAL_METHOD_CALL.

## <a name="oncancel"></a>Asyncbase::oncancel –

Při přepisu v odvozené třídě, zruší asynchronní operace.

```cpp
virtual void OnCancel(
   void
) = 0;
```

## <a name="onclose"></a>Asyncbase::onclose –

Při přepisu v odvozené třídě, ukončí asynchronní operaci.

```cpp
virtual void OnClose(
   void
) = 0;
```

## <a name="onstart"></a>Asyncbase::ONSTART –

Při přepisu v odvozené třídě, spustí asynchronní operaci.

```cpp
virtual HRESULT OnStart(
   void
) = 0;
```

## <a name="put-id"></a>Asyncbase::put_id –

Nastaví popisovač asynchronní operace.

```cpp
STDMETHOD(
   put_Id
)(const unsigned int id);
```

### <a name="parameters"></a>Parametry

*id*<br/>
Popisovač nenulovou hodnotu.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak E_INVALIDARG nebo E_ILLEGAL_METHOD_CALL.

## <a name="putoncomplete"></a>Asyncbase::putoncomplete –

Nastaví adresu obslužné rutiny události dokončení se zadanou hodnotou.

```cpp
STDMETHOD(
   PutOnComplete
)(TComplete* completeHandler);
```

### <a name="parameters"></a>Parametry

*completeHandler*<br/>
Adresy, ke kterému je nastavena obslužná rutina události dokončení.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě E_ILLEGAL_METHOD_CALL.

## <a name="putonprogress"></a>AsyncBase::PutOnProgress

Nastaví adresu průběh obslužné rutiny události se zadanou hodnotou.

```cpp
STDMETHOD(
   PutOnProgress
)(TProgress* progressHandler);
```

### <a name="parameters"></a>Parametry

*progressHandler*<br/>
Adresy, ke kterému je nastavena obslužná rutina události průběh.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě E_ILLEGAL_METHOD_CALL.

## <a name="start"></a>Asyncbase::Start –

Spustí asynchronní operaci.

```cpp
STDMETHOD(
   Start
)(void);
```

### <a name="return-value"></a>Návratová hodnota

S_OK Pokud operaci spuštění nebo je již spuštěna; v opačném případě E_ILLEGAL_STATE_CHANGE.

### <a name="remarks"></a>Poznámky

`Start()` je chráněný, který není externě viditelný, protože asynchronní operace "horkými start" před vrácením řízení volajícímu metody.

## <a name="trytransitiontocompleted"></a>Asyncbase::trytransitiontocompleted –

Určuje, zda aktuální asynchronní operace byla dokončena.

```cpp
bool TryTransitionToCompleted(
   void
);
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud dokončení asynchronní operace; v opačném případě **false**.

## <a name="trytransitiontoerror"></a>Asyncbase::trytransitiontoerror –

Určuje, zda kód zadanou chybovou můžete upravit stavu došlo k vnitřní chybě.

```cpp
bool TryTransitionToError(
   const HRESULT error
);
```

### <a name="parameters"></a>Parametry

*error*<br/>
Chyba HRESULT.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud státu došlo k vnitřní chybě byla změněné; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Tato operace změní chybový stav, pouze v případě, že chybový stav je již nastavena na hodnotu S_OK. Tato operace nemá žádný vliv, pokud chybový stav je již chyba, zrušena, Dokončeno nebo Uzavřeno.
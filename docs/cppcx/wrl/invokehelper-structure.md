---
title: InvokeHelper – struktura
ms.date: 10/18/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::InvokeHelper
- event/Microsoft::WRL::Details::InvokeHelper::callback_
- event/Microsoft::WRL::Details::InvokeHelper::Invoke
- event/Microsoft::WRL::Details::InvokeHelper::InvokeHelper
helpviewer_keywords:
- Microsoft::WRL::Details::InvokeHelper structure
- Microsoft::WRL::Details::callback_ data member
- Microsoft::WRL::Details::Invoke method
- Microsoft::WRL::Details::InvokeHelper, constructor
ms.assetid: 555ad2bc-4dd6-4e65-a2e2-1242c395f0e5
ms.openlocfilehash: 9cb4e166628a6b5e7671494446d467e73c9f8cc3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371376"
---
# <a name="invokehelper-structure"></a>InvokeHelper – struktura

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename TDelegateInterface, typename TCallback, unsigned int argCount>
struct InvokeHelper;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 0> :
    public Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 1> :
    public Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 2> :
    public Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 3> :
    public Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 4> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 5> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 6> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 7> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 8> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 9> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;
```

### <a name="parameters"></a>Parametry

*TDelegateInterface*<br/>
Typ rozhraní delegáta.

*Zpětné volání T*<br/>
Typ funkce obslužné rutiny události.

*argCount*<br/>
Počet argumentů v `InvokeHelper` specializaci.

## <a name="remarks"></a>Poznámky

Poskytuje implementaci metody `Invoke()` na základě zadaného počtu a typu argumentů.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

Name (Název)     | Popis
-------- | -----------------------------------------------------------------------------
`Traits` | Synonymum pro třídu, která definuje typ každého argumentu obslužné rutiny události.

### <a name="public-constructors"></a>Veřejné konstruktory

Name (Název)                                        | Popis
------------------------------------------- | -------------------------------------------------------
[InvokeHelper::InvokeHelper](#invokehelper) | Inicializuje novou instanci třídy. `InvokeHelper`

### <a name="public-methods"></a>Veřejné metody

Name (Název)                            | Popis
------------------------------- | -----------------------------------------------------------------------------------
[InvokeHelper::Vyvolat](#invoke) | Zavolá obslužnou rutinu události, jejíž podpis obsahuje zadaný počet argumentů.

### <a name="public-data-members"></a>Veřejné datové členy

Name (Název)                                 | Popis
------------------------------------ | ----------------------------------------------------------
[InvokeHelper::callback_](#callback) | Představuje obslužnou rutinu události, která má být volána, když dojde k události.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`InvokeHelper`

## <a name="requirements"></a>Požadavky

**Záhlaví:** event.h

**Obor názvů:** Microsoft::WRL::Details

## <a name="invokehelpercallback_"></a><a name="callback"></a>InvokeHelper::callback_

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
TCallback callback_;
```

### <a name="remarks"></a>Poznámky

Představuje obslužnou rutinu události, která má být volána, když dojde k události.

Parametr `TCallback` šablony určuje typ obslužné rutiny události.

## <a name="invokehelperinvoke"></a><a name="invoke"></a>InvokeHelper::Vyvolat

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
STDMETHOD(
   Invoke
)();
STDMETHOD(
   Invoke
)(typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
```

### <a name="parameters"></a>Parametry

*arg1*<br/>
Argument 1.

*arg2*<br/>
Argument 2.

*arg3*<br/>
Argument 3.

*arg4*<br/>
Argument 4.

*arg5*<br/>
Argument 5.

*arg6*<br/>
Argument 6.

*arg7*<br/>
Argument 7.

*arg8*<br/>
Argument 8.

*arg9*<br/>
Argument 9.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak HRESULT, který popisuje chybu.

### <a name="remarks"></a>Poznámky

Zavolá obslužnou rutinu události, jejíž podpis obsahuje zadaný počet argumentů.

## <a name="invokehelperinvokehelper"></a><a name="invokehelper"></a>InvokeHelper::InvokeHelper

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
explicit InvokeHelper(
   TCallback callback
);
```

### <a name="parameters"></a>Parametry

*Zpětného volání*<br/>
Obslužná rutina události.

### <a name="remarks"></a>Poznámky

Inicializuje novou instanci třídy. `InvokeHelper`

Parametr `TCallback` šablony určuje typ obslužné rutiny události.

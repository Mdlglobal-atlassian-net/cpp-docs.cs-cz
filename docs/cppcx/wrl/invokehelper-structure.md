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
ms.openlocfilehash: 3fcba210d4018d22487d234b437acfee3634cec6
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58786707"
---
# <a name="invokehelper-structure"></a>InvokeHelper – struktura

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

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

*TCallback*<br/>
Typ funkce obslužné rutiny události.

*argCount*<br/>
Počet argumentů v `InvokeHelper` specializace.

## <a name="remarks"></a>Poznámky

Poskytuje implementaci `Invoke()` metoda na základě zadané číslo a typ argumentů.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

Name     | Popis
-------- | -----------------------------------------------------------------------------
`Traits` | Synonymum pro třídu, která definuje typ každého argumentu obslužné rutiny události.

### <a name="public-constructors"></a>Veřejné konstruktory

Name                                        | Popis
------------------------------------------- | -------------------------------------------------------
[Invokehelper::invokehelper –](#invokehelper) | Inicializuje novou instanci třídy `InvokeHelper` třídy.

### <a name="public-methods"></a>Veřejné metody

Name                            | Popis
------------------------------- | -----------------------------------------------------------------------------------
[Invokehelper::Invoke –](#invoke) | Volá obslužnou rutinu události, jehož předpis obsahuje zadaný počet argumentů.

### <a name="public-data-members"></a>Veřejné datové členy

Name                                 | Popis
------------------------------------ | ----------------------------------------------------------
[Invokehelper::callback_ –](#callback) | Reprezentuje obslužnou rutinu události pro volání při výskytu události.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`InvokeHelper`

## <a name="requirements"></a>Požadavky

**Záhlaví:** event.h

**Namespace:** Microsoft::WRL::Details

## <a name="callback"></a>Invokehelper::callback_ –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
TCallback callback_;
```

### <a name="remarks"></a>Poznámky

Reprezentuje obslužnou rutinu události pro volání při výskytu události.

`TCallback` Parametr šablony určuje typ obslužné rutiny události.

## <a name="invoke"></a>Invokehelper::Invoke –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

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

S_OK v případě úspěchu; v opačném případě popisující chybu HRESULT.

### <a name="remarks"></a>Poznámky

Volá obslužnou rutinu události, jehož předpis obsahuje zadaný počet argumentů.

## <a name="invokehelper"></a>Invokehelper::invokehelper –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
explicit InvokeHelper(
   TCallback callback
);
```

### <a name="parameters"></a>Parametry

*callback*<br/>
Obslužné rutiny události.

### <a name="remarks"></a>Poznámky

Inicializuje novou instanci třídy `InvokeHelper` třídy.

`TCallback` Parametr šablony určuje typ obslužné rutiny události.

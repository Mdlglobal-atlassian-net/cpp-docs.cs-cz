---
title: Invokehelper – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/21/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::InvokeHelper
- event/Microsoft::WRL::Details::InvokeHelper::callback_
- event/Microsoft::WRL::Details::InvokeHelper::Invoke
- event/Microsoft::WRL::Details::InvokeHelper::InvokeHelper
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::InvokeHelper structure
- Microsoft::WRL::Details::callback_ data member
- Microsoft::WRL::Details::Invoke method
- Microsoft::WRL::Details::InvokeHelper, constructor
ms.assetid: 555ad2bc-4dd6-4e65-a2e2-1242c395f0e5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6eccc9a7eacf9cdd3b98796f575d966b7b566864
ms.sourcegitcommit: edb46b0239a0e616af4ec58906e12338c3e8d2c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47169534"
---
# <a name="invokehelper-structure"></a>InvokeHelper – struktura

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template<
   typename TDelegateInterface,
   typename TCallback,
   unsigned int argCount
>
struct InvokeHelper;
template<
   typename TDelegateInterface,
   typename TCallback
>
struct InvokeHelper<TDelegateInterface, TCallback, 0> : public Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;
template<
   typename TDelegateInterface,
   typename TCallback
>
struct InvokeHelper<TDelegateInterface, TCallback, 1> : public Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;
template<
   typename TDelegateInterface,
   typename TCallback
>
struct InvokeHelper<TDelegateInterface, TCallback, 2> : public Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;
template<
   typename TDelegateInterface,
   typename TCallback
>
struct InvokeHelper<TDelegateInterface, TCallback, 3> : public Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;
template<
   typename TDelegateInterface,
   typename TCallback
>
struct InvokeHelper<TDelegateInterface, TCallback, 4> : Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;
template<
   typename TDelegateInterface,
   typename TCallback
>
struct InvokeHelper<TDelegateInterface, TCallback, 5> : Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;
template<
   typename TDelegateInterface,
   typename TCallback
>
struct InvokeHelper<TDelegateInterface, TCallback, 6> : Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;
template<
   typename TDelegateInterface,
   typename TCallback
>
struct InvokeHelper<TDelegateInterface, TCallback, 7> : Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;
template<
   typename TDelegateInterface,
   typename TCallback
>
struct InvokeHelper<TDelegateInterface, TCallback, 8> : Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;
template<
   typename TDelegateInterface,
   typename TCallback
>
struct InvokeHelper<TDelegateInterface, TCallback, 9> : Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;
```

### <a name="parameters"></a>Parametry

*TDelegateInterface*<br/>
*TCallback*  
Typ funkce obslužné rutiny události.

*argCount*<br/>
Počet argumentů v `InvokeHelper` specializace.

## <a name="remarks"></a>Poznámky

Poskytuje implementaci `Invoke()` metoda na základě zadané číslo a typ argumentů.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

Název     | Popis
-------- | -----------------------------------------------------------------------------
`Traits` | Synonymum pro třídu, která definuje typ každého argumentu obslužné rutiny události.

### <a name="public-constructors"></a>Veřejné konstruktory

Název                                        | Popis
------------------------------------------- | -------------------------------------------------------
[Invokehelper::invokehelper –](#invokehelper) | Inicializuje novou instanci třídy `InvokeHelper` třídy.

### <a name="public-methods"></a>Veřejné metody

Název                            | Popis
------------------------------- | -----------------------------------------------------------------------------------
[Invokehelper::Invoke –](#invoke) | Volá obslužnou rutinu události, jehož předpis obsahuje zadaný počet argumentů.

### <a name="public-data-members"></a>Veřejné datové členy

Název                                 | Popis
------------------------------------ | ----------------------------------------------------------
[Invokehelper::callback_ –](#callback) | Reprezentuje obslužnou rutinu události pro volání při výskytu události.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`InvokeHelper`

## <a name="requirements"></a>Požadavky

**Záhlaví:** event.h

**Namespace:** Microsoft::WRL:: details –

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

*zpětné volání*<br/>
Obslužné rutiny události.

### <a name="remarks"></a>Poznámky

Inicializuje novou instanci třídy `InvokeHelper` třídy.

`TCallback` Parametr šablony určuje typ obslužné rutiny události.

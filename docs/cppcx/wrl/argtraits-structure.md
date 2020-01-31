---
title: ArgTraits – struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraits
- event/Microsoft::WRL::Details::ArgTraits::args
helpviewer_keywords:
- Microsoft::WRL::Details::ArgTraits structure
- Microsoft::WRL::Details::ArgTraits::args constant
ms.assetid: 58ae4115-c1bc-48c8-b01b-e60554841c30
ms.openlocfilehash: c13e7fec3289b66b40e44f91404a50cba7a473b1
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821711"
---
# <a name="argtraits-structure"></a>ArgTraits – struktura

Podporuje infrastrukturu WRL a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename TMemberFunction>
struct ArgTraits;

template<typename TDelegateInterface>
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(void)>;

template<typename TDelegateInterface, typename TArg1>
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1)>;

template<typename TDelegateInterface, typename TArg1, typename TArg2>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2, TArg3)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5, TArg6)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6,
    typename TArg7
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6,
    typename TArg7,
    typename TArg8
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7, TArg8)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6,
    typename TArg7,
    typename TArg8,
    typename TArg9
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7, TArg8, TArg9)>;
```

### <a name="parameters"></a>Parametry

*TMemberFunction*<br/>
Parametr TypeName pro strukturu ArgTraits –, která nemůže odpovídat žádnému podpisu metody `Invoke`.

*TDelegateInterface*<br/>
Rozhraní delegáta.

*TArg1*<br/>
Typ prvního argumentu metody `Invoke`.

*TArg2*<br/>
Typ druhého argumentu metody `Invoke`.

*TArg3*<br/>
Typ třetího argumentu metody `Invoke`.

*TArg4*<br/>
Typ čtvrtého argumentu metody `Invoke`.

*TArg5*<br/>
Typ pátého argumentu metody `Invoke`.

*TArg6*<br/>
Typ šestého argumentu metody `Invoke`.

*TArg7*<br/>
Typ sedmého argumentu metody `Invoke`.

*TArg8*<br/>
Typ osmého argumentu metody `Invoke`.

*TArg9*<br/>
Typ devátého argumentu metody `Invoke`.

## <a name="remarks"></a>Poznámky

Struktura `ArgTraits` deklaruje zadané rozhraní delegáta a anonymní členskou funkci, která má zadaný počet parametrů.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

Name       | Popis
---------- | ----------------------
`Arg1Type` | Definice TypeDef pro TArg1.
`Arg2Type` | Definice TypeDef pro TArg2.
`Arg3Type` | Definice TypeDef pro TArg3.
`Arg4Type` | Definice TypeDef pro TArg4.
`Arg5Type` | Definice TypeDef pro TArg5.
`Arg6Type` | Definice TypeDef pro TArg6.
`Arg7Type` | Definice TypeDef pro TArg7.
`Arg8Type` | Definice TypeDef pro TArg8.
`Arg9Type` | Definice TypeDef pro TArg9.

### <a name="public-constants"></a>Veřejné konstanty

Name                     | Popis
------------------------ | ---------------------------------------------------------------------------------------
[ArgTraits –:: args](#args) | Zaznamenává počet parametrů v metodě `Invoke` rozhraní delegáta.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ArgTraits`

## <a name="requirements"></a>Požadavky

**Záhlaví:** Event. h

**Obor názvů:** Microsoft:: WRL::D etails

## <a name="args"></a>ArgTraits –:: args

Podporuje infrastrukturu WRL a není určena pro použití přímo v kódu.

```cpp
static const int args = -1;
```

### <a name="remarks"></a>Poznámky

Zaznamenává počet parametrů v metodě `Invoke` rozhraní delegáta. Pokud `args` rovná-1, nemůžete pro podpis `Invoke` metody najít žádnou shodu.

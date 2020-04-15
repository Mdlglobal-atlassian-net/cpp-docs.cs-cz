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
ms.openlocfilehash: 16c44d861ebbbc98fa1bffb62a00d1989c0c803c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377163"
---
# <a name="argtraits-structure"></a>ArgTraits – struktura

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

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

*Funkce TMember*<br/>
Parametr Typename pro strukturu ArgTraits, `Invoke` která nemůže odpovídat podpisu metody.

*TDelegateInterface*<br/>
Rozhraní delegáta.

*Targ1*<br/>
Typ prvního argumentu `Invoke` metody.

*Targ2*<br/>
Typ druhého argumentu `Invoke` metody.

*Targ3*<br/>
Typ třetího argumentu `Invoke` metody.

*Targ4*<br/>
Typ čtvrtého argumentu `Invoke` metody.

*Targ5*<br/>
Typ pátého argumentu `Invoke` metody.

*Targ6*<br/>
Typ šestého argumentu `Invoke` metody.

*Targ7 (Fr.)*<br/>
Typ sedmého argumentu `Invoke` metody.

*Targ8*<br/>
Typ osmého argumentu `Invoke` metody.

*Targ9*<br/>
Typ devátého argumentu `Invoke` metody.

## <a name="remarks"></a>Poznámky

Struktura `ArgTraits` deklaruje zadané rozhraní delegáta a anonymní členská funkce, která má zadaný počet parametrů.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

Name (Název)       | Popis
---------- | ----------------------
`Arg1Type` | Typedef pro TArg1.
`Arg2Type` | Typedef pro TArg2.
`Arg3Type` | Typedef pro TArg3.
`Arg4Type` | Typedef pro TArg4.
`Arg5Type` | Typedef pro TArg5.
`Arg6Type` | Typedef pro TArg6.
`Arg7Type` | Typedef pro TArg7.
`Arg8Type` | Typedef pro TArg8.
`Arg9Type` | Typedef pro TArg9.

### <a name="public-constants"></a>Veřejné konstanty

Name (Název)                     | Popis
------------------------ | ---------------------------------------------------------------------------------------
[ArgTraits::args](#args) | Udržuje počet parametrů na metodu `Invoke` delegáta rozhraní.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ArgTraits`

## <a name="requirements"></a>Požadavky

**Záhlaví:** event.h

**Obor názvů:** Microsoft::WRL::Details

## <a name="argtraitsargs"></a><a name="args"></a>ArgTraits::args

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
static const int args = -1;
```

### <a name="remarks"></a>Poznámky

Udržuje počet parametrů na metodu `Invoke` delegáta rozhraní. Pokud `args` se rovná -1, může existovat `Invoke` žádná shoda pro podpis metody.

---
title: Implementuje strukturu
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements
- implements/Microsoft::WRL::Implements::CanCastTo
- implements/Microsoft::WRL::Implements::CastToUnknown
- implements/Microsoft::WRL::Implements::FillArrayWithIid
- implements/Microsoft::WRL::Implements::IidCount
helpviewer_keywords:
- Microsoft::WRL::Implements structure
- Microsoft::WRL::Implements::CanCastTo method
- Microsoft::WRL::Implements::CastToUnknown method
- Microsoft::WRL::Implements::FillArrayWithIid method
- Microsoft::WRL::Implements::IidCount method
ms.assetid: 29b13e90-34d4-4a0b-babd-5187c9eb0c36
ms.openlocfilehash: 0ce6e9193107cbd0d033d99b257e41004b4343a8
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821854"
---
# <a name="implements-structure"></a>Implementuje strukturu

Implementuje `QueryInterface` a `GetIid` pro zadaná rozhraní.

## <a name="syntax"></a>Syntaxe

```cpp
template <
    typename I0,
    typename I1 = Details::Nil,
    typename I2 = Details::Nil,
    typename I3 = Details::Nil,
    typename I4 = Details::Nil,
    typename I5 = Details::Nil,
    typename I6 = Details::Nil,
    typename I7 = Details::Nil,
    typename I8 = Details::Nil,
    typename I9 = Details::Nil
>
struct __declspec(novtable) Implements :
    Details::ImplementsHelper<
        RuntimeClassFlags<WinRt>,
        typename Details::InterfaceListHelper<
            I0, I1, I2, I3, I4, I5, I6, I7, I8, I9
        >::TypeT
    >,
    Details::ImplementsBase;

template <
    int flags,
    typename I0,
    typename I1,
    typename I2,
    typename I3,
    typename I4,
    typename I5,
    typename I6,
    typename I7,
    typename I8
>
struct __declspec(novtable) Implements<
        RuntimeClassFlags<flags>,
        I0, I1, I2, I3, I4, I5, I6, I7, I8> :
    Details::ImplementsHelper<
        RuntimeClassFlags<flags>,
        typename Details::InterfaceListHelper<
            I0, I1, I2, I3, I4, I5, I6, I7, I8
        >::TypeT
    >,
    Details::ImplementsBase;
```

### <a name="parameters"></a>Parametry

*I0*<br/>
ID rozhraní zeroth Závaznou

*I1*<br/>
První ID rozhraní. (Volitelné)

*I2*<br/>
Druhé ID rozhraní. (Volitelné)

*I3*<br/>
IDENTIFIKÁTOR třetího rozhraní. (Volitelné)

*I4*<br/>
Čtvrté ID rozhraní. (Volitelné)

*I5*<br/>
Pátý identifikátor rozhraní. (Volitelné)

*I6*<br/>
Šesté ID rozhraní. (Volitelné)

*I7*<br/>
ID sedmého rozhraní. (Volitelné)

*I8*<br/>
Osmá ID rozhraní. (Volitelné)

*I9*<br/>
ID devátého rozhraní. (Volitelné)

*Flag*<br/>
Příznaky konfigurace pro třídu. Jeden nebo více výčtů [RuntimeClassType –](runtimeclasstype-enumeration.md) , které jsou zadány ve struktuře [RuntimeClassFlags](runtimeclassflags-structure.md) .

## <a name="remarks"></a>Poznámky

Je odvozen ze seznamu zadaných rozhraní a implementuje pomocné šablony pro `QueryInterface` a `GetIid`.

Každý *I0* prostřednictvím parametru rozhraní *i9* se musí odvozovat buď z `IUnknown`, `IInspectable`, nebo šablony [ChainInterfaces](chaininterfaces-structure.md) . Parametr *Flags* určuje, zda je pro `IUnknown` nebo `IInspectable`vygenerována podpora.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

| Name        | Popis                               |
| ----------- | ----------------------------------------- |
| `ClassFlags`| Synonymum pro `RuntimeClassFlags<WinRt>`. |

### <a name="protected-methods"></a>Chráněné metody

| Name                                              | Popis                                                                                                   |
| ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| [Implementuje:: Cancastto –](#cancastto)               | Získá ukazatel na zadané rozhraní.                                                                    |
| [Implementuje:: Casttounknown –](#casttounknown)       | Získá ukazatel na základní `IUnknown` rozhraní.                                                        |
| [Implementuje:: Fillarraywithiid –](#fillarraywithiid) | Vloží ID rozhraní určené aktuálním parametrem šablony zeroth do určeného prvku Array. |

### <a name="protected-constants"></a>Chráněné konstanty

| Name                              | Popis                                    |
| --------------------------------- | ---------------------------------------------- |
| [Implementuje:: Iidcount –](#iidcount) | Obsahuje počet implementovaných ID rozhraní. |

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`I0`

`ChainInterfaces`

`I0`

`ImplementsBase`

`ImplementsHelper`

`Implements`

## <a name="requirements"></a>Požadavky

**Hlavička:** Implements. h

**Obor názvů:** Microsoft:: WRL

## <a name="cancastto"></a>Implementuje:: Cancastto –

Získá ukazatel na zadané rozhraní.

```cpp
__forceinline HRESULT CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parametry

*riid*<br/>
Odkaz na ID rozhraní.

*ppv*<br/>
V případě úspěchu ukazatel na rozhraní určené parametrem *riid*.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě hodnota HRESULT, která označuje chybu, například E_NOINTERFACE.

### <a name="remarks"></a>Poznámky

Toto je interní pomocná funkce, která provádí operaci QueryInterface.

## <a name="casttounknown"></a>Implementuje:: Casttounknown –

Získá ukazatel na základní `IUnknown` rozhraní.

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Návratová hodnota

Tato operace vždy uspěje a vrací ukazatel `IUnknown`.

### <a name="remarks"></a>Poznámky

Vnitřní pomocná funkce.

## <a name="fillarraywithiid"></a>Implementuje:: Fillarraywithiid –

Vloží ID rozhraní určené aktuálním parametrem šablony zeroth do určeného prvku Array.

```cpp
__forceinline static void FillArrayWithIid(
   unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Parametry

*index*<br/>
Index založený na nule, který označuje počáteční prvek pole pro tuto operaci. Po dokončení této operace se *index* zvýší o 1.

*IID*<br/>
Pole typu IID.

### <a name="remarks"></a>Poznámky

Vnitřní pomocná funkce.

## <a name="iidcount"></a>Implementuje:: Iidcount –

Obsahuje počet implementovaných ID rozhraní.

```cpp
static const unsigned long IidCount;
```

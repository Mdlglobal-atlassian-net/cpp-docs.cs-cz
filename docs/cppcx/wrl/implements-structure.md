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
ms.openlocfilehash: 223f37d7cabbd0b8cd238582773c05d7b9eaabf6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371412"
---
# <a name="implements-structure"></a>Implementuje strukturu

`QueryInterface` Implementuje `GetIid` a pro zadaná rozhraní.

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
Zeroth ID rozhraní. (Povinné)

*I1*<br/>
První ID rozhraní. (Nepovinné)

*I2*<br/>
Druhé ID rozhraní. (Nepovinné)

*I3*<br/>
Třetí ID rozhraní. (Nepovinné)

*I4*<br/>
Čtvrté ID rozhraní. (Nepovinné)

*I5*<br/>
Páté ID rozhraní. (Nepovinné)

*I6*<br/>
Šesté ID rozhraní. (Nepovinné)

*I7*<br/>
Sedmé ID rozhraní. (Nepovinné)

*I8*<br/>
Osmé ID rozhraní. (Nepovinné)

*I9*<br/>
Deváté ID rozhraní. (Nepovinné)

*příznaky*<br/>
Příznaky konfigurace pro třídu. Jeden nebo více výčtů [Typu RuntimeClassType,](runtimeclasstype-enumeration.md) které jsou zadány ve struktuře [RuntimeClassFlags.](runtimeclassflags-structure.md)

## <a name="remarks"></a>Poznámky

Odvozuje ze seznamu zadaných rozhraní a implementuje pomocné šablony pro `QueryInterface` a `GetIid`.

Každý parametr rozhraní *I0* až *I9* musí být odvozen buď z `IUnknown`, `IInspectable`nebo ze šablony [ChainInterfaces.](chaininterfaces-structure.md) Parametr *flags* určuje, zda je `IUnknown` generována podpora pro nebo `IInspectable`.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

| Name (Název)        | Popis                               |
| ----------- | ----------------------------------------- |
| `ClassFlags`| Synonymum `RuntimeClassFlags<WinRt>`pro . |

### <a name="protected-methods"></a>Chráněné metody

| Name (Název)                                              | Popis                                                                                                   |
| ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| [Implementace::CanCastTo](#cancastto)               | Získá ukazatel na zadané rozhraní.                                                                    |
| [Implementuje::CastToUnknown](#casttounknown)       | Získá ukazatel na `IUnknown` základní rozhraní.                                                        |
| [Implementace::FillArrayWithId](#fillarraywithiid) | Vloží ID rozhraní určené aktuálním parametrem šablony nulty do zadaného prvku pole. |

### <a name="protected-constants"></a>Chráněné konstanty

| Name (Název)                              | Popis                                    |
| --------------------------------- | ---------------------------------------------- |
| [Implementace::IidCount](#iidcount) | Obsahuje počet implementovaných ID rozhraní. |

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`I0`

`ChainInterfaces`

`I0`

`ImplementsBase`

`ImplementsHelper`

`Implements`

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Obor názvů:** Microsoft::WRL

## <a name="implementscancastto"></a><a name="cancastto"></a>Implementace::CanCastTo

Získá ukazatel na zadané rozhraní.

```cpp
__forceinline HRESULT CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parametry

*riid řekl:*<br/>
Odkaz na ID rozhraní.

*Ppv*<br/>
V případě úspěchu ukazatel na rozhraní určené *riid*.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak HRESULT, který označuje chybu, například E_NOINTERFACE.

### <a name="remarks"></a>Poznámky

Toto je interní pomocná funkce, která provádí operaci QueryInterface.

## <a name="implementscasttounknown"></a><a name="casttounknown"></a>Implementuje::CastToUnknown

Získá ukazatel na `IUnknown` základní rozhraní.

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Návratová hodnota

Tato operace vždy úspěšné `IUnknown` a vrátí ukazatel.

### <a name="remarks"></a>Poznámky

Interní pomocná funkce.

## <a name="implementsfillarraywithiid"></a><a name="fillarraywithiid"></a>Implementace::FillArrayWithId

Vloží ID rozhraní určené aktuálním parametrem šablony nulty do zadaného prvku pole.

```cpp
__forceinline static void FillArrayWithIid(
   unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Parametry

*Index*<br/>
Index založený na nule, který označuje počáteční prvek pole pro tuto operaci. Po dokončení této operace *index* se zpřísní o 1.

*IIDs*<br/>
Pole typu IID.

### <a name="remarks"></a>Poznámky

Interní pomocná funkce.

## <a name="implementsiidcount"></a><a name="iidcount"></a>Implementace::IidCount

Obsahuje počet implementovaných ID rozhraní.

```cpp
static const unsigned long IidCount;
```

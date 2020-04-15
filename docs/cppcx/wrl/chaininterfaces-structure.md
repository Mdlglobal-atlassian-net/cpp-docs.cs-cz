---
title: ChainInterfaces – struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces
- implements/Microsoft::WRL::ChainInterfaces::CanCastTo
- implements/Microsoft::WRL::ChainInterfaces::CastToUnknown
- implements/Microsoft::WRL::ChainInterfaces::FillArrayWithIid
- implements/Microsoft::WRL::ChainInterfaces::IidCount
- implements/Microsoft::WRL::ChainInterfaces::Verify
helpviewer_keywords:
- Microsoft::WRL::ChainInterfaces structure
- Microsoft::WRL::ChainInterfaces::CanCastTo method
- Microsoft::WRL::ChainInterfaces::CastToUnknown method
- Microsoft::WRL::ChainInterfaces::FillArrayWithIid method
- Microsoft::WRL::ChainInterfaces::IidCount constant
- Microsoft::WRL::ChainInterfaces::Verify method
ms.assetid: d7415b59-5468-4bef-a3fd-8d82b12f0e9c
ms.openlocfilehash: dd1af3fb5c1079a40d8248dc71ae4972537aa856
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372650"
---
# <a name="chaininterfaces-structure"></a>ChainInterfaces – struktura

Určuje ověřovací a inicializační funkce, které lze použít pro sadu ID rozhraní.

## <a name="syntax"></a>Syntaxe

```cpp
template <
    typename I0,
    typename I1,
    typename I2 = Details::Nil,
    typename I3 = Details::Nil,
    typename I4 = Details::Nil,
    typename I5 = Details::Nil,
    typename I6 = Details::Nil,
    typename I7 = Details::Nil,
    typename I8 = Details::Nil,
    typename I9 = Details::Nil
>
struct ChainInterfaces : I0;

template <
    typename DerivedType,
    typename BaseType,
    bool hasImplements,
    typename I1,
    typename I2,
    typename I3,
    typename I4,
    typename I5,
    typename I6,
    typename I7,
    typename I8,
    typename I9
>
struct ChainInterfaces<
    MixIn<
        DerivedType,
        BaseType,
        hasImplements
    >, I1, I2, I3, I4, I5, I6, I7, I8, I9
>;
```

### <a name="parameters"></a>Parametry

*I0*<br/>
(Povinné) ID rozhraní 0.

*I1*<br/>
(Povinné) ID rozhraní 1.

*I2*<br/>
(Nepovinné) ID rozhraní 2.

*I3*<br/>
(Nepovinné) ID rozhraní 3.

*I4*<br/>
(Nepovinné) ID rozhraní 4.

*I5*<br/>
(Nepovinné) ID rozhraní 5.

*I6*<br/>
(Nepovinné) ID rozhraní 6.

*I7*<br/>
(Nepovinné) ID rozhraní 7.

*I8*<br/>
(Nepovinné) ID rozhraní 8.

*I9*<br/>
(Nepovinné) ID rozhraní 9.

*DerivedType*<br/>
Odvozený typ.

*BaseType*<br/>
Základní typ odvozeného typu.

*hasImplements*<br/>
Logická hodnota, která pokud **true**, znamená, že nelze použít [MixIn](mixin-structure.md) strukturu s třídou, která není odvozena z [implements](implements-structure.md) stucture.

## <a name="members"></a>Členové

### <a name="protected-methods"></a>Chráněné metody

Name (Název)                                                   | Popis
------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ChainInterfaces::CanCastTo](#cancastto)               | Označuje, zda zadané ID rozhraní může být přetypováno `ChainInterface` do každé specializace definované parametry šablony.
[ChainInterfaces::CastToUnknown](#casttounknown)       | Přetypovat ukazatel rozhraní typu definovaného parametrem šablony *I0* na ukazatel na `IUnknown`.
[ChainInterfaces::FillArrayWithId](#fillarraywithiid) | Uloží ID rozhraní definované parametrem šablony *I0* do zadaného umístění v zadaném poli ID rozhraní.
[ChainInterfaces::Ověřit](#verify)                     | Ověří, že každé rozhraní definované parametry šablony *I0* až `IInspectable` *I9* dědí z `IUnknown` a/nebo a že *I0* dědí z *I1* až *I9*.

### <a name="protected-constants"></a>Chráněné konstanty

Name (Název)                                   | Popis
-------------------------------------- | -----------------------------------------------------------------------------------------------------------------
[ChainInterfaces::IidCount](#iidcount) | Celkový počet ID rozhraní obsažených v rozhraních určených parametry šablony *I0* až *I9*.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`I0`

`ChainInterfaces`

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Obor názvů:** Microsoft::WRL

## <a name="chaininterfacescancastto"></a><a name="cancastto"></a>ChainInterfaces::CanCastTo

Označuje, zda lze zadané ID rozhraní přetypovat do každé specializace definované nevýchozími parametry šablony.

```cpp
__forceinline bool CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parametry

*riid řekl:*<br/>
ID rozhraní.

*Ppv*<br/>
Ukazatel na poslední ID rozhraní, které bylo úspěšně přetypováno.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud všechny operace obsazení úspěšné; jinak **false**.

## <a name="chaininterfacescasttounknown"></a><a name="casttounknown"></a>ChainInterfaces::CastToUnknown

Přetypovat ukazatel rozhraní typu definovaného parametrem šablony *I0* na ukazatel na `IUnknown`.

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `IUnknown`.

## <a name="chaininterfacesfillarraywithiid"></a><a name="fillarraywithiid"></a>ChainInterfaces::FillArrayWithId

Uloží ID rozhraní definované parametrem šablony *I0* do zadaného umístění v zadaném poli ID rozhraní.

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Parametry

*Index*<br/>
Ukazatel na hodnotu indexu do pole *IIDs.*

*IIDs*<br/>
Pole ID rozhraní.

## <a name="chaininterfacesiidcount"></a><a name="iidcount"></a>ChainInterfaces::IidCount

Celkový počet ID rozhraní obsažených v rozhraních určených parametry šablony *I0* až *I9*.

```cpp
static const unsigned long IidCount = Details::InterfaceTraits<I0>::IidCount + Details::InterfaceTraits<I1>::IidCount + Details::InterfaceTraits<I2>::IidCount + Details::InterfaceTraits<I3>::IidCount + Details::InterfaceTraits<I4>::IidCount + Details::InterfaceTraits<I5>::IidCount + Details::InterfaceTraits<I6>::IidCount + Details::InterfaceTraits<I7>::IidCount + Details::InterfaceTraits<I8>::IidCount + Details::InterfaceTraits<I9>::IidCount;
```

### <a name="return-value"></a>Návratová hodnota

Celkový počet ID rozhraní.

### <a name="remarks"></a>Poznámky

Parametry šablony *I0* a *I1* jsou povinné a parametry *I2* až *I9* jsou volitelné. Počet IID každého rozhraní je obvykle 1.

## <a name="chaininterfacesverify"></a><a name="verify"></a>ChainInterfaces::Ověřit

Ověří, že každé rozhraní definované parametry šablony *I0* až `IInspectable` *I9* dědí z `IUnknown` a/nebo a že *I0* dědí z *I1* až *I9*.

```cpp
WRL_NOTHROW __forceinline static void Verify();
```

### <a name="remarks"></a>Poznámky

Pokud ověřovací operace selže, `static_assert` vydává chybovou zprávu popisující selhání.

Parametry šablony *I0* a *I1* jsou povinné a parametry *I2* až *I9* jsou volitelné.

---
title: Chaininterfaces – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/28/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces
- implements/Microsoft::WRL::ChainInterfaces::CanCastTo
- implements/Microsoft::WRL::ChainInterfaces::CastToUnknown
- implements/Microsoft::WRL::ChainInterfaces::FillArrayWithIid
- implements/Microsoft::WRL::ChainInterfaces::IidCount
- implements/Microsoft::WRL::ChainInterfaces::Verify
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::ChainInterfaces structure
- Microsoft::WRL::ChainInterfaces::CanCastTo method
- Microsoft::WRL::ChainInterfaces::CastToUnknown method
- Microsoft::WRL::ChainInterfaces::FillArrayWithIid method
- Microsoft::WRL::ChainInterfaces::IidCount constant
- Microsoft::WRL::ChainInterfaces::Verify method
ms.assetid: d7415b59-5468-4bef-a3fd-8d82b12f0e9c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a80b9afd8f2db895440d12776173c559e41c2cfe
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2018
ms.locfileid: "48234863"
---
# <a name="chaininterfaces-structure"></a>ChainInterfaces – struktura

Určuje, ověřování a Inicializace funkce, které mohou být použity na sadu rozhraní ID.

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
struct ChainInterfaces<MixIn<DerivedType, BaseType, hasImplements>, I1, I2, I3, I4, I5, I6, I7, I8, I9>;
```

### <a name="parameters"></a>Parametry

*I0*<br/>
(Povinné) ID rozhraní: 0.

*I1*<br/>
(Povinné) ID rozhraní: 1.

*I2*<br/>
(Volitelné) Rozhraní s ID 2.

*I3*<br/>
(Volitelné) ID rozhraní 3.

*TYP I4*<br/>
(Volitelné) ID rozhraní 4.

*I5*<br/>
(Volitelné) ID rozhraní 5.

*I6*<br/>
(Volitelné) ID rozhraní 6.

*I7*<br/>
(Volitelné) Rozhraní ID 7.

*I8*<br/>
(Volitelné) ID rozhraní 8.

*I9*<br/>
(Volitelné) ID rozhraní 9.

*DerivedType*<br/>
Odvozeného typu.

*BaseType*<br/>
Základní typ odvozeného typu.

*hasImplements*<br/>
Logická hodnota, že pokud `true`, znamená, že nemůžete použít [MixIn](../windows/mixin-structure.md) strukturu s třídou, která není odvozena od [implementuje](../windows/implements-structure.md) stucture.

## <a name="members"></a>Členové

### <a name="protected-methods"></a>Chráněné metody

Název                                                   | Popis
------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[Chaininterfaces::cancastto –](#cancastto)               | Určuje, jestli ID zadané rozhraní může být převeden na jednotlivé specializace určené `ChainInterface` parametry šablony.
[Chaininterfaces::casttounknown –](#casttounknown)       | Přetypování ukazatele rozhraní typu definované *I0* parametr šablony na ukazatel na `IUnknown`.
[Chaininterfaces::fillarraywithiid –](#fillarraywithiid) | Ukládá ID rozhraní určené *I0* parametr šablony v zadaném umístění v zadaném poli ID rozhraní.
[Chaininterfaces::Verify –](#verify)                     | Ověřuje, že každé rozhraní určené parametry šablony *I0* prostřednictvím *I9* dědí z `IUnknown` a/nebo `IInspectable`a že *I0* dědí z *I1* prostřednictvím *I9*.

### <a name="protected-constants"></a>Chráněné konstanty

Název                                   | Popis
-------------------------------------- | -----------------------------------------------------------------------------------------------------------------
[ChainInterfaces::IidCount](#iidcount) | Celkový počet rozhraní ID, které jsou součástí rozhraní určené parametry šablony *I0* prostřednictvím *I9*.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`I0`

`ChainInterfaces`

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL

## <a name="cancastto"></a>Chaininterfaces::cancastto –

Určuje, zda ID zadané rozhraní může být převeden na jednotlivé specializace určené parametry jiné než výchozí šablony.

```cpp
__forceinline bool CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parametry

*riid*<br/>
Identifikátor rozhraní.

*ppv*<br/>
Ukazatel na poslední ID rozhraní, který byl úspěšně převeden.

### <a name="return-value"></a>Návratová hodnota

`true` Pokud se úspěšně dokončila všechny operace přetypování; v opačném případě `false`.

## <a name="casttounknown"></a>Chaininterfaces::casttounknown –

Přetypování ukazatele rozhraní typu definované *I0* parametr šablony na ukazatel na `IUnknown`.

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `IUnknown`.

## <a name="fillarraywithiid"></a>Chaininterfaces::fillarraywithiid –

Ukládá ID rozhraní určené *I0* parametr šablony v zadaném umístění v zadaném poli ID rozhraní.

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Parametry

*index*<br/>
Ukazatel na hodnotu indexu do *IID* pole.

*IID*<br/>
Pole ID rozhraní.

## <a name="iidcount"></a>ChainInterfaces::IidCount

Celkový počet rozhraní ID, které jsou součástí rozhraní určené parametry šablony *I0* prostřednictvím *I9*.

```cpp
static const unsigned long IidCount = Details::InterfaceTraits<I0>::IidCount + Details::InterfaceTraits<I1>::IidCount + Details::InterfaceTraits<I2>::IidCount + Details::InterfaceTraits<I3>::IidCount + Details::InterfaceTraits<I4>::IidCount + Details::InterfaceTraits<I5>::IidCount + Details::InterfaceTraits<I6>::IidCount + Details::InterfaceTraits<I7>::IidCount + Details::InterfaceTraits<I8>::IidCount + Details::InterfaceTraits<I9>::IidCount;
```

### <a name="return-value"></a>Návratová hodnota

Celkový počet ID rozhraní.

### <a name="remarks"></a>Poznámky

Parametry šablony *I0* a *I1* jsou povinné a parametry *I2* prostřednictvím *I9* jsou volitelné. Počet IID každé rozhraní, které je obvykle 1.

## <a name="verify"></a>Chaininterfaces::Verify –

Ověřuje, že každé rozhraní určené parametry šablony *I0* prostřednictvím *I9* dědí z `IUnknown` a/nebo `IInspectable`a že *I0* dědí z *I1* prostřednictvím *I9*.

```cpp
WRL_NOTHROW __forceinline static void Verify();
```

### <a name="remarks"></a>Poznámky

Pokud se ověření nezdaří, `static_assert` vydá chybovou zprávu s popisem chyby.

Parametry šablony *I0* a *I1* jsou povinné a parametry *I2* prostřednictvím *I9* jsou volitelné.

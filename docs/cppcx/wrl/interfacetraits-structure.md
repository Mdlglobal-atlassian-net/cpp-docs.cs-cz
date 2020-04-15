---
title: InterfaceTraits – struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits
- implements/Microsoft::WRL::Details::InterfaceTraits::CanCastTo
- implements/Microsoft::WRL::Details::InterfaceTraits::CastToBase
- implements/Microsoft::WRL::Details::InterfaceTraits::CastToUnknown
- implements/Microsoft::WRL::Details::InterfaceTraits::FillArrayWithIid
- implements/Microsoft::WRL::Details::InterfaceTraits::IidCount
- implements/Microsoft::WRL::Details::InterfaceTraits::Verify
helpviewer_keywords:
- Microsoft::WRL::Details::InterfaceTraits structure
- Microsoft::WRL::Details::InterfaceTraits::CanCastTo method
- Microsoft::WRL::Details::InterfaceTraits::CastToBase method
- Microsoft::WRL::Details::InterfaceTraits::CastToUnknown method
- Microsoft::WRL::Details::InterfaceTraits::FillArrayWithIid method
- Microsoft::WRL::Details::InterfaceTraits::IidCount constant
- Microsoft::WRL::Details::InterfaceTraits::Verify method
ms.assetid: ede0c284-19a7-4892-9738-ff3da4923d0a
ms.openlocfilehash: 17f743a38af3ddc600a55e38905d19868d076a22
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371375"
---
# <a name="interfacetraits-structure"></a>InterfaceTraits – struktura

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename I0>
struct __declspec(novtable) InterfaceTraits;

template<typename CloakedType>
struct __declspec(novtable) InterfaceTraits<
    CloakedIid<CloakedType>
>;

template<>
struct __declspec(novtable) InterfaceTraits<Nil>;
```

### <a name="parameters"></a>Parametry

*I0*<br/>
Název rozhraní.

*Maskovaný typ*<br/>
Pro `RuntimeClass` `Implements` rozhraní `ChainInterfaces`, které nebude v seznamu podporovaných ID rozhraní.

## <a name="remarks"></a>Poznámky

Implementuje společné charakteristiky rozhraní.

Druhá šablona je specializace pro maskované rozhraní. Třetí šablona je specializace na nulové parametry.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a><a name="public-typedefs"></a>Veřejné typedefs

Name (Název)   | Popis
------ | ------------------------------------------
`Base` | Synonymum pro parametr šablony *I0.*

### <a name="public-methods"></a>Veřejné metody

Name (Název)                                                   | Popis
------------------------------------------------------ | ----------------------------------------------------------------------------------------
[InterfaceTraits::CanCastTo](#cancastto)               | Označuje, zda lze zadaný ukazatel `Base`přetypovat na ukazatel na .
[InterfaceTraits::CastToBase](#casttobase)             | Přetypovat zadaný ukazatel `Base`na ukazatel na .
[InterfaceTraits::CastToUnknown](#casttounknown)       | Přetypovat zadaný ukazatel `IUnknown`na ukazatel na .
[InterfaceTraits::FillArrayWithId](#fillarraywithiid) | Přiřadí ID `Base` rozhraní prvku pole určenému argumentem indexu.
[InterfaceTraits::Ověřit](#verify)                     | Ověří, `Base` že je správně odvozen.

### <a name="public-constants"></a>Veřejné konstanty

Name (Název)                                   | Popis
-------------------------------------- | ---------------------------------------------------------------------------------------
[InterfaceTraits::IidCount](#iidcount) | Obsahuje počet ID rozhraní přidružených `InterfaceTraits` k aktuálnímu objektu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`InterfaceTraits`

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Obor názvů:** Microsoft::WRL::Details

## <a name="interfacetraitscancastto"></a><a name="cancastto"></a>InterfaceTraits::CanCastTo

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
template<typename T>
static __forceinline bool CanCastTo(
   _In_ T* ptr,
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parametry

*Ptr*<br/>
Název ukazatele na typ.

*riid řekl:*<br/>
ID rozhraní `Base`aplikace .

*Ppv*<br/>
Pokud je tato operace úspěšná, *ppv* odkazuje na rozhraní určené rozhraním `Base`. V opačném případě je `nullptr` *ppv* nastavena na .

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je tato operace úspěšná a `Base` *ptr* je přetypována na ukazatel ; jinak **false**.

### <a name="remarks"></a>Poznámky

Označuje, zda lze zadaný ukazatel `Base`přetypovat na ukazatel na .

Další informace `Base`o tématu naleznete v části [Public Typedefs.](#public-typedefs)

## <a name="interfacetraitscasttobase"></a><a name="casttobase"></a>InterfaceTraits::CastToBase

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
template<typename T>
static __forceinline Base* CastToBase(
   _In_ T* ptr
);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ parametru *ptr*.

*Ptr*<br/>
Ukazatel na typ *T*.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `Base`.

### <a name="remarks"></a>Poznámky

Přetypovat zadaný ukazatel `Base`na ukazatel na .

Další informace `Base`o tématu naleznete v části [Public Typedefs.](#public-typedefs)

## <a name="interfacetraitscasttounknown"></a><a name="casttounknown"></a>InterfaceTraits::CastToUnknown

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
template<typename T>
static __forceinline IUnknown* CastToUnknown(
   _In_ T* ptr
);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ parametru *ptr*.

*Ptr*<br/>
Ukazatel na typ *T*.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na IUnknown, `Base` z kterého je odvozen.

### <a name="remarks"></a>Poznámky

Přetypovat zadaný ukazatel `IUnknown`na ukazatel na .

Další informace `Base`o tématu naleznete v části [Public Typedefs.](#public-typedefs)

## <a name="interfacetraitsfillarraywithiid"></a><a name="fillarraywithiid"></a>InterfaceTraits::FillArrayWithId

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Parametry

*Index*<br/>
Ukazatel na pole, které obsahuje hodnotu indexu s nulou.

*IIDs*<br/>
Pole ID rozhraní.

### <a name="remarks"></a>Poznámky

Přiřadí ID `Base` rozhraní prvku pole určenému argumentem indexu.

Na rozdíl od názvu tohoto rozhraní API je změněn pouze jeden prvek pole; není celé pole.

Další informace `Base`o tématu naleznete v části [Public Typedefs.](#public-typedefs)

## <a name="interfacetraitsiidcount"></a><a name="iidcount"></a>InterfaceTraits::IidCount

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
static const unsigned long IidCount = 1;
```

### <a name="remarks"></a>Poznámky

Obsahuje počet ID rozhraní přidružených `InterfaceTraits` k aktuálnímu objektu.

## <a name="interfacetraitsverify"></a><a name="verify"></a>InterfaceTraits::Ověřit

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
__forceinline static void Verify();
```

### <a name="remarks"></a>Poznámky

Ověří, `Base` že je správně odvozen.

Další informace `Base`o tématu naleznete v části [Public Typedefs.](#public-typedefs)

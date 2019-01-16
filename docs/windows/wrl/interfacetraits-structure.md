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
ms.openlocfilehash: e8222ccaca9572331412b90e696829568eedcf8e
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334774"
---
# <a name="interfacetraits-structure"></a>InterfaceTraits – struktura

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

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

*CloakedType*<br/>
Pro `RuntimeClass`, `Implements` a `ChainInterfaces`, rozhraní, které nesmí být v seznamu nepodporuje ID rozhraní.

## <a name="remarks"></a>Poznámky

Implementuje běžné vlastnosti rozhraní.

Druhá šablona je specializací skrytá rozhraní. Třetí šablony je specializací Nil parametrů.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

Název   | Popis
------ | ------------------------------------------
`Base` | Synonymum pro *I0* parametr šablony.

### <a name="public-methods"></a>Veřejné metody

Název                                                   | Popis
------------------------------------------------------ | ----------------------------------------------------------------------------------------
[Interfacetraits::cancastto –](#cancastto)               | Určuje, zda je zadaný ukazatel může být převeden na ukazatel na `Base`.
[Interfacetraits::casttobase –](#casttobase)             | Přetypování zadaný ukazatel na ukazatel na `Base`.
[Interfacetraits::casttounknown –](#casttounknown)       | Přetypování zadaný ukazatel na ukazatel na `IUnknown`.
[Interfacetraits::fillarraywithiid –](#fillarraywithiid) | Přiřadí Identifikátor rozhraní `Base` k prvku pole určená argumentem indexu.
[InterfaceTraits::Verify](#verify)                     | Ověřuje, že `Base` správně pochází.

### <a name="public-constants"></a>Veřejné konstanty

Název                                   | Popis
-------------------------------------- | ---------------------------------------------------------------------------------------
[InterfaceTraits::IidCount](#iidcount) | Obsahuje počet rozhraní přidružené k aktuální ID `InterfaceTraits` objektu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`InterfaceTraits`

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="cancastto"></a>Interfacetraits::cancastto –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
template<typename T>
static __forceinline bool CanCastTo(
   _In_ T* ptr,
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parametry

*ptr*<br/>
Název ukazatele na typ.

*riid*<br/>
ID rozhraní `Base`.

*ppv*<br/>
Pokud je tato operace úspěšná, *ppv* odkazuje na rozhraní určené typem `Base`. V opačném případě *ppv* je nastavena na `nullptr`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud je tato operace úspěšná a *ptr* přetypovat na ukazatel na `Base`; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Určuje, zda je zadaný ukazatel může být převeden na ukazatel na `Base`.

Další informace o `Base`, najdete v článku [veřejné definice TypeDef](#public-typedefs) oddílu.

## <a name="casttobase"></a>Interfacetraits::casttobase –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
template<typename T>
static __forceinline Base* CastToBase(
   _In_ T* ptr
);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ parametru *ptr*.

*ptr*<br/>
Ukazatel na typ *T*.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `Base`.

### <a name="remarks"></a>Poznámky

Přetypování zadaný ukazatel na ukazatel na `Base`.

Další informace o `Base`, najdete v článku [veřejné definice TypeDef](#public-typedefs) oddílu.

## <a name="casttounknown"></a>Interfacetraits::casttounknown –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
template<typename T>
static __forceinline IUnknown* CastToUnknown(
   _In_ T* ptr
);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ parametru *ptr*.

*ptr*<br/>
Ukazatel na typ *T*.

### <a name="return-value"></a>Návratová hodnota

Ukazatel rozhraní IUnknown odkud `Base` pochází.

### <a name="remarks"></a>Poznámky

Přetypování zadaný ukazatel na ukazatel na `IUnknown`.

Další informace o `Base`, najdete v článku [veřejné definice TypeDef](#public-typedefs) oddílu.

## <a name="fillarraywithiid"></a>Interfacetraits::fillarraywithiid –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Parametry

*index*<br/>
Ukazatel na pole, které obsahuje hodnotu index založený na nule.

*iids*<br/>
Pole ID rozhraní.

### <a name="remarks"></a>Poznámky

Přiřadí Identifikátor rozhraní `Base` k prvku pole určená argumentem indexu.

Rozporu s názvem toto rozhraní API se mění pouze jedno pole elementu; není celého pole.

Další informace o `Base`, najdete v článku [veřejné definice TypeDef](#public-typedefs) oddílu.

## <a name="iidcount"></a>InterfaceTraits::IidCount

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
static const unsigned long IidCount = 1;
```

### <a name="remarks"></a>Poznámky

Obsahuje počet rozhraní přidružené k aktuální ID `InterfaceTraits` objektu.

## <a name="verify"></a>Interfacetraits::Verify –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
__forceinline static void Verify();
```

### <a name="remarks"></a>Poznámky

Ověřuje, že `Base` správně pochází.

Další informace o `Base`, najdete v článku [veřejné definice TypeDef](#public-typedefs) oddílu.

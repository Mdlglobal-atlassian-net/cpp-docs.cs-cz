---
title: ImplementsHelper – struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ImplementsHelper
- implements/Microsoft::WRL::Details::ImplementsHelper::CanCastTo
- implements/Microsoft::WRL::Details::ImplementsHelper::CastToUnknown
- implements/Microsoft::WRL::Details::ImplementsHelper::FillArrayWithIid
- implements/Microsoft::WRL::Details::ImplementsHelper::IidCount
helpviewer_keywords:
- Microsoft::WRL::Details::ImplementsHelper structure
- Microsoft::WRL::Details::ImplementsHelper::CanCastTo method
- Microsoft::WRL::Details::ImplementsHelper::CastToUnknown method
- Microsoft::WRL::Details::ImplementsHelper::FillArrayWithIid method
- Microsoft::WRL::Details::ImplementsHelper::IidCount constant
ms.assetid: b857ba80-81bd-4e53-92b6-210991954243
ms.openlocfilehash: 250a59152e9b41eb48c453caaa696fdc8ca3d3b4
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58786983"
---
# <a name="implementshelper-structure"></a>ImplementsHelper – struktura

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename RuntimeClassFlagsT, typename ILst, bool IsDelegateToClass>
friend struct Details::ImplementsHelper;
```

### <a name="parameters"></a>Parametry

*RuntimeClassFlagsT*<br/>
Pole, která určuje jeden nebo více příznaků [runtimeclasstype –](runtimeclasstype-enumeration.md) enumerátory.

*ILst*<br/>
Seznam ID rozhraní.

*IsDelegateToClass*<br/>
Zadejte **true** Pokud aktuální instancí třídy `Implements` je základní třídou ID prvního rozhraní v *ILst*; v opačném případě **false**.

## <a name="remarks"></a>Poznámky

Pomáhá implementovat [implementuje](implements-structure.md) struktury.

Tato šablona prochází seznam rozhraní a přidá je jako základní třídy a jako informace nutné k povolení `QueryInterface`.

## <a name="members"></a>Členové

### <a name="protected-methods"></a>Chráněné metody

Name                                                    | Popis
------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------
[Implementshelper::cancastto –](#cancastto)               | Získá ukazatel na ID zadané rozhraní.
[Implementshelper::casttounknown –](#casttounknown)       | Získá ukazatel na základní `IUnknown` rozhraní pro aktuální `Implements` struktury.
[Implementshelper::fillarraywithiid –](#fillarraywithiid) | Vloží ID rozhraní určené parametrem aktuální ID nultého šablona do určeného pole elementu.
[ImplementsHelper::IidCount](#iidcount)                 | Obsahuje počet implementovaných rozhraní ID v aktuálním `Implements` objektu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ImplementsHelper`

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="cancastto"></a>Implementshelper::cancastto –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
HRESULT CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);

HRESULT CanCastTo(
   _In_ const IID &iid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parametry

*riid*<br/>
Odkaz na identifikátor rozhraní.

*ppv*<br/>
Pokud je tato operace úspěšná, ukazatel na rozhraní určené *riid* nebo *iid*.

*iid*<br/>
Odkaz na identifikátor rozhraní.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu.

### <a name="remarks"></a>Poznámky

Získá ukazatel na ID zadané rozhraní.

## <a name="casttounknown"></a>Implementshelper::casttounknown –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na základní `IUnknown` rozhraní.

### <a name="remarks"></a>Poznámky

Získá ukazatel na základní `IUnknown` rozhraní pro aktuální `Implements` struktury.

## <a name="fillarraywithiid"></a>Implementshelper::fillarraywithiid –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
void FillArrayWithIid(
   _Inout_ unsigned long *index,
   _Inout_ IID* iids) throw();
```

### <a name="parameters"></a>Parametry

*index*<br/>
Z nuly vycházející index určující počáteční prvek pole pro tuto operaci. Po dokončení této operace *index* zvyšuje o 1.

*iids*<br/>
Pole typu IID.

### <a name="remarks"></a>Poznámky

Vloží ID rozhraní určené parametrem aktuální ID nultého šablona do určeného pole elementu.

## <a name="iidcount"></a>ImplementsHelper::IidCount

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
static const unsigned long IidCount;
```

### <a name="remarks"></a>Poznámky

Obsahuje počet implementovaných rozhraní ID v aktuálním `Implements` objektu.

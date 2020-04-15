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
ms.openlocfilehash: e33842f574df5617fb40c5b3f6bb8324d5ba7c1e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371401"
---
# <a name="implementshelper-structure"></a>ImplementsHelper – struktura

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename RuntimeClassFlagsT, typename ILst, bool IsDelegateToClass>
friend struct Details::ImplementsHelper;
```

### <a name="parameters"></a>Parametry

*RuntimeClassFlagsT*<br/>
Pole příznaků, které určuje jeden nebo více čítačů výčtu [RuntimeClassType.](runtimeclasstype-enumeration.md)

*ILst*<br/>
Seznam ID rozhraní.

*IsDelegateToClass*<br/>
Zadejte **hodnotu true,** pokud `Implements` je aktuální instance základní třídy prvního ID rozhraní v *ILst*; jinak **false**.

## <a name="remarks"></a>Poznámky

Pomáhá implementovat [implementaci implementuje](implements-structure.md) struktury.

Tato šablona prochází seznam rozhraní a přidá je jako základní třídy a jako informace nezbytné k povolení `QueryInterface`.

## <a name="members"></a>Členové

### <a name="protected-methods"></a>Chráněné metody

Name (Název)                                                    | Popis
------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------
[ImplementsHelper::CanCastTo](#cancastto)               | Získá ukazatel na zadané ID rozhraní.
[ImplementsHelper::CastToUnknown](#casttounknown)       | Získá ukazatel na `IUnknown` základní rozhraní `Implements` pro aktuální strukturu.
[ImplementsHelper::FillArrayWithId](#fillarraywithiid) | Vloží ID rozhraní určené aktuálním parametrem šablony nulty do zadaného prvku pole.
[ImplementsHelper::IidCount](#iidcount)                 | Obsahuje počet implementovaných ID rozhraní `Implements` v aktuálním objektu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ImplementsHelper`

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Obor názvů:** Microsoft::WRL::Details

## <a name="implementshelpercancastto"></a><a name="cancastto"></a>ImplementsHelper::CanCastTo

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

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

*riid řekl:*<br/>
Odkaz na ID rozhraní.

*Ppv*<br/>
Pokud je tato operace úspěšná, ukazatel na rozhraní určené *riid* nebo *iid*.

*Iid*<br/>
Odkaz na ID rozhraní.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak HRESULT, který označuje chybu.

### <a name="remarks"></a>Poznámky

Získá ukazatel na zadané ID rozhraní.

## <a name="implementshelpercasttounknown"></a><a name="casttounknown"></a>ImplementsHelper::CastToUnknown

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `IUnknown` základní rozhraní.

### <a name="remarks"></a>Poznámky

Získá ukazatel na `IUnknown` základní rozhraní `Implements` pro aktuální strukturu.

## <a name="implementshelperfillarraywithiid"></a><a name="fillarraywithiid"></a>ImplementsHelper::FillArrayWithId

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
void FillArrayWithIid(
   _Inout_ unsigned long *index,
   _Inout_ IID* iids) throw();
```

### <a name="parameters"></a>Parametry

*Index*<br/>
Index založený na nule, který označuje počáteční prvek pole pro tuto operaci. Po dokončení této operace *index* se zpřísní o 1.

*IIDs*<br/>
Pole ID typu.

### <a name="remarks"></a>Poznámky

Vloží ID rozhraní určené aktuálním parametrem šablony nulty do zadaného prvku pole.

## <a name="implementshelperiidcount"></a><a name="iidcount"></a>ImplementsHelper::IidCount

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
static const unsigned long IidCount;
```

### <a name="remarks"></a>Poznámky

Obsahuje počet implementovaných ID rozhraní `Implements` v aktuálním objektu.

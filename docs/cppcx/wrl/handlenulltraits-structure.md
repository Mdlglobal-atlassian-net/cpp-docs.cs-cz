---
title: HANDLENullTraits – struktura
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::Close
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::GetInvalidValue
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::Close method
- Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::GetInvalidValue method
ms.assetid: 88a29a14-c516-40cb-a0ca-ee897a668623
ms.openlocfilehash: 41e06cc50f36a077a34d992c416a543e5bf9b593
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371479"
---
# <a name="handlenulltraits-structure"></a>HANDLENullTraits – struktura

Definuje společné charakteristiky neinicializovaného popisovače.

## <a name="syntax"></a>Syntaxe

```cpp
struct HANDLENullTraits;
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

Name (Název)   | Popis
------ | ---------------------
`Type` | Synonymum pro HANDLE.

### <a name="public-methods"></a>Veřejné metody

Name (Název)                                                  | Popis
----------------------------------------------------- | -----------------------------
[HANDLENullTraits::Zavřít](#close)                     | Zavře zadaný popisovač.
[HANDLENullTraits::GetInvalidValue](#getinvalidvalue) | Představuje neplatný popisovač.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`HANDLENullTraits`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Obor názvů:** Microsoft::WRL::Obálky::HandleTraits

## <a name="handlenulltraitsclose"></a><a name="close"></a>HANDLENullTraits::Zavřít

Zavře zadaný popisovač.

```cpp
inline static bool Close(
   _In_ Type h
);
```

### <a name="parameters"></a>Parametry

*H*<br/>
Rukojeť zavřít.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud popisovač *h* úspěšně uzavřen; jinak **false**.

## <a name="handlenulltraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>HANDLENullTraits::GetInvalidValue

Představuje neplatný popisovač.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí hodnotu `nullptr`.

---
title: Struktura HANDLETraits
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::Close
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::GetInvalidValue
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits structure
- Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::Close method
- Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::GetInvalidValue method
ms.assetid: 22963e88-d857-4624-9182-7c986daff722
ms.openlocfilehash: 604098cd3289722767117910d6e44e272dcb8b77
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371451"
---
# <a name="handletraits-structure"></a>Struktura HANDLETraits

Definuje společné charakteristiky úchytu.

## <a name="syntax"></a>Syntaxe

```cpp
struct HANDLETraits;
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

Name (Název)   | Popis
------ | ---------------------
`Type` | Synonymum pro HANDLE.

### <a name="public-methods"></a>Veřejné metody

Name (Název)                                              | Popis
------------------------------------------------- | -----------------------------
[HANDLETraits::Zavřít](#close)                     | Zavře zadaný popisovač.
[HANDLETraits::GetInvalidValue](#getinvalidvalue) | Představuje neplatný popisovač.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`HANDLETraits`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Obor názvů:** Microsoft::WRL::Obálky::HandleTraits

## <a name="handletraitsclose"></a><a name="close"></a>HANDLETraits::Zavřít

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

## <a name="handletraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>HANDLETraits::GetInvalidValue

Představuje neplatný popisovač.

```cpp
inline static HANDLE GetInvalidValue();
```

### <a name="return-value"></a>Návratová hodnota

Vždy se vrátí INVALID_HANDLE_VALUE. (INVALID_HANDLE_VALUE je definovánsystémem Windows.)

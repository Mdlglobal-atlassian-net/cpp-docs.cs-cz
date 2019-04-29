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
ms.openlocfilehash: 4dd2cde62d36c46926e703e6fb649e2ae4ef7811
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398365"
---
# <a name="handletraits-structure"></a>Struktura HANDLETraits

Definuje běžné vlastnosti popisovač.

## <a name="syntax"></a>Syntaxe

```cpp
struct HANDLETraits;
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

Název   | Popis
------ | ---------------------
`Type` | Synonymum pro POPISOVAČ.

### <a name="public-methods"></a>Veřejné metody

Název                                              | Popis
------------------------------------------------- | -----------------------------
[Handletraits::Close –](#close)                     | Zavře určený.
[Handletraits::getinvalidvalue –](#getinvalidvalue) | Představuje neplatný popisovač.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`HANDLETraits`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="close"></a>Handletraits::Close –

Zavře určený.

```cpp
inline static bool Close(
   _In_ Type h
);
```

### <a name="parameters"></a>Parametry

*h*<br/>
Obslužná rutina zavřete.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** pokud zpracování *h* zavření úspěšně; v opačném případě **false**.

## <a name="getinvalidvalue"></a>Handletraits::getinvalidvalue –

Představuje neplatný popisovač.

```cpp
inline static HANDLE GetInvalidValue();
```

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí INVALID_HANDLE_VALUE. (INVALID_HANDLE_VALUE je definován ve Windows.)

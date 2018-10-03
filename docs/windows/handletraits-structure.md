---
title: Handletraits – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/27/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::Close
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::GetInvalidValue
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits structure
- Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::Close method
- Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::GetInvalidValue method
ms.assetid: 22963e88-d857-4624-9182-7c986daff722
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 33181b2cf477c3f753eacf63110a426b36e62b31
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235266"
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

`true` Pokud zpracování *h* zavření úspěšně; v opačném případě `false`.

## <a name="getinvalidvalue"></a>Handletraits::getinvalidvalue –

Představuje neplatný popisovač.

```cpp
inline static HANDLE GetInvalidValue();
```

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí INVALID_HANDLE_VALUE. (INVALID_HANDLE_VALUE je definován ve Windows.)

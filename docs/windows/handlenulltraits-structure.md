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
ms.openlocfilehash: d70425f414b998eb67e3937c2c126dd3eda0c00d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571363"
---
# <a name="handlenulltraits-structure"></a>HANDLENullTraits – struktura

Definuje běžné vlastnosti neinicializovaný popisovač.

## <a name="syntax"></a>Syntaxe

```cpp
struct HANDLENullTraits;
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

Název   | Popis
------ | ---------------------
`Type` | Synonymum pro POPISOVAČ.

### <a name="public-methods"></a>Veřejné metody

Název                                                  | Popis
----------------------------------------------------- | -----------------------------
[Handlenulltraits::Close –](#close)                     | Zavře určený.
[Handlenulltraits::getinvalidvalue –](#getinvalidvalue) | Představuje neplatný popisovač.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`HANDLENullTraits`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="close"></a>Handlenulltraits::Close –

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

## <a name="getinvalidvalue"></a>Handlenulltraits::getinvalidvalue –

Představuje neplatný popisovač.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí `nullptr`.

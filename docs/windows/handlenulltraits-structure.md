---
title: Handlenulltraits – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/27/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::Close
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::GetInvalidValue
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::Close method
- Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::GetInvalidValue method
ms.assetid: 88a29a14-c516-40cb-a0ca-ee897a668623
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 517e861020c48d08f40c9683822e3df23cbf38a2
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235890"
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

`true` Pokud zpracování *h* zavření úspěšně; v opačném případě `false`.

## <a name="getinvalidvalue"></a>Handlenulltraits::getinvalidvalue –

Představuje neplatný popisovač.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí `nullptr`.

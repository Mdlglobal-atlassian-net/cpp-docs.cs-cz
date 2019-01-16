---
title: EnableIf – struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::EnableIf
helpviewer_keywords:
- EnableIf structure
ms.assetid: 7825b283-e6b2-4f39-a4b9-c03bcd431b8e
ms.openlocfilehash: 7b65b11b9a67ba69ca546e9bf5c169f3f2b61765
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334747"
---
# <a name="enableif-structure"></a>EnableIf – struktura

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <bool b, typename T = void>
struct EnableIf;

template <typename T>
struct EnableIf<true, T>;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ.

*b*<br/>
Logický výraz.

## <a name="remarks"></a>Poznámky

Datový člen typu určené druhý parametr šablony, pokud je vyhodnocen jako první parametr šablony definuje **true**.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|`type`|Pokud parametr šablony *b* vyhodnotí jako **true**, částečná specializace definuje datový člen `type` typu `T`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`EnableIf`

## <a name="requirements"></a>Požadavky

**Záhlaví:** internal.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Details – obor názvů](microsoft-wrl-details-namespace.md)
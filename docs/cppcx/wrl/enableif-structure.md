---
title: EnableIf – struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::EnableIf
helpviewer_keywords:
- EnableIf structure
ms.assetid: 7825b283-e6b2-4f39-a4b9-c03bcd431b8e
ms.openlocfilehash: 44c6293b56e9e03c23d0d8cebf2a112e6fcf3664
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214029"
---
# <a name="enableif-structure"></a>EnableIf – struktura

Podporuje infrastrukturu WRL a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <bool b, typename T = void>
struct EnableIf;

template <typename T>
struct EnableIf<true, T>;
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Typ.

*b*<br/>
Logický výraz.

## <a name="remarks"></a>Poznámky

Definuje datový člen typu určeného druhým parametrem šablony, pokud je první parametr šablony vyhodnocen jako **true**.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Název|Popis|
|----------|-----------------|
|`type`|Pokud je parametr šablony *b* vyhodnocen jako **true**, Částečná specializace definuje datový člen `type` být typu `T`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`EnableIf`

## <a name="requirements"></a>Požadavky

**Záhlaví:** interní. h

**Obor názvů:** Microsoft:: WRL::D etails

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Details – obor názvů](microsoft-wrl-details-namespace.md)

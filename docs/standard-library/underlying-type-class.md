---
title: underlying_type – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::underlying_type
helpviewer_keywords:
- underlying_type
ms.assetid: 691ddce3-2677-4480-bd35-d933fab85d3e
ms.openlocfilehash: 23e5e9bc5406265f49fca2ed220c597cb32e2a9a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50609700"
---
# <a name="underlyingtype-class"></a>underlying_type – třída

Vytvoří základní celočíselného typu pro typ výčtu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct underlying_type;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ, který chcete upravit.

## <a name="remarks"></a>Poznámky

`type` Definice typu člena třídy šablony názvů základního celočíselného typu *T*, když *T* je číselného typu, jinak neexistuje žádný člen typedef `type`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>

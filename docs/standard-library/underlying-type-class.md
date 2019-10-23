---
title: underlying_type – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::underlying_type
helpviewer_keywords:
- underlying_type
ms.assetid: 691ddce3-2677-4480-bd35-d933fab85d3e
ms.openlocfilehash: ea4768d78047112a7584ca49b0e4487fad55a970
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688846"
---
# <a name="underlying_type-class"></a>underlying_type – třída

Vytvoří základní celočíselný typ pro typ výčtu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct underlying_type;
```

### <a name="parameters"></a>Parametry

*T* \
Typ, který chcete upravit.

## <a name="remarks"></a>Poznámky

@No__t_0 typedef člena šablony třídy pojmenuje základní celočíselný typ *t*, pokud *t* je typ výčtu, jinak neexistuje žádný člen typedef `type`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)

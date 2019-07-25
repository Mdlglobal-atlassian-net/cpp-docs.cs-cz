---
title: is_move_constructible – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_move_constructible
helpviewer_keywords:
- is_move_constructible
ms.assetid: becdf076-7419-488d-a335-78adf2478b9b
ms.openlocfilehash: c83ed4365fd0e73a7daa8b9894c5e85f20387a79
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456108"
---
# <a name="ismoveconstructible-class"></a>is_move_constructible – třída

Testuje, zda typ obsahuje konstruktor Move.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>Parametry

*Š*\
Typ, který se má vyhodnotit

## <a name="remarks"></a>Poznámky

Predikát typu, který se vyhodnotí jako true, pokud typ *T* může být vytvořen pomocí operace přesunutí. Tento predikát je ekvivalentem `is_constructible<T, T&&>`.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)

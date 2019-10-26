---
title: is_move_constructible – třída
ms.date: 10/24/2019
f1_keywords:
- type_traits/std::is_move_constructible
helpviewer_keywords:
- is_move_constructible
ms.assetid: becdf076-7419-488d-a335-78adf2478b9b
ms.openlocfilehash: 9585a932a34a24769201aaa379525a9b4c181e41
ms.sourcegitcommit: 33a898bf976c65f998b4e88a84765a0cef4193a8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920090"
---
# <a name="is_move_constructible-class"></a>is_move_constructible – třída

Testuje, zda lze typ sestavit pomocí operace přesunutí.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>Parametry

*T* \
Typ, který má být vyhodnocen.

## <a name="remarks"></a>Poznámky

Predikát typu, který se vyhodnotí jako **true** , pokud typ *T* může být vytvořen pomocí operace přesunutí. Tento predikát je ekvivalentní `is_constructible<T, T&&>`. Typ *T* , který nemá konstruktor Move, ale má kopírovací konstruktor, který přijímá `const T&` argument, splňuje `std::is_move_constructible`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)

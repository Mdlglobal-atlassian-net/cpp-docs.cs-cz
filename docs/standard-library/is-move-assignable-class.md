---
title: is_move_assignable – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_move_assignable
helpviewer_keywords:
- is_move_assignable
ms.assetid: f33137f2-0639-4912-8745-bc0f9fd18d28
ms.openlocfilehash: 8563db51eeb1988697b3e07a1a8673a777783e38
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456119"
---
# <a name="ismoveassignable-class"></a>is_move_assignable – třída

Testuje, zda lze typ přesunout přiřazeno.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_move_assignable;
```

### <a name="parameters"></a>Parametry

*Š*\
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Typ je přesunutý, pokud odkaz na rvalue typ může být přiřazený odkaz na typ. Predikát typu je ekvivalentem `is_assignable<T&, T&&>`. Přesunoutelné typy zahrnují referenční skalární typy a typy tříd, které mají buď operátory vygenerované kompilátorem, nebo uživatelsky definované operátory přiřazení přesunutí.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)

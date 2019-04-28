---
title: is_move_assignable Class
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_move_assignable
helpviewer_keywords:
- is_move_assignable
ms.assetid: f33137f2-0639-4912-8745-bc0f9fd18d28
ms.openlocfilehash: da4734507bac14ecf0278117deb7668518305be0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351063"
---
# <a name="ismoveassignable-class"></a>is_move_assignable Class

Testuje, zda může být typu přesuňte přiřazené.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_move_assignable;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Typ je přiřaditelný přesunout, pokud odkaz rvalue na typ, je možné přiřadit na odkaz na typ. Predikát typu je ekvivalentní `is_assignable<T&, T&&>`. Přesuňte přiřadit typy zahrnují označím Skalární typy a typy tříd, které se mají generované kompilátorem nebo uživatelem definované operátory přiřazení přesunutí.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>

---
title: is_trivially_move_assignable – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_move_assignable
helpviewer_keywords:
- is_trivially_move_assignable
ms.assetid: 374f7322-0706-4bc1-a1a5-4191d0315e28
ms.openlocfilehash: b25d16658def4e3cf620ab707d2dabacb2620f33
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50435536"
---
# <a name="istriviallymoveassignable-class"></a>is_trivially_move_assignable – třída

Ověřuje, zda tento typ nemá operátor přiřazení přesunutí triviální.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_trivially_move_assignable;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Instance predikátu typu obsahuje hodnotu true, pokud typ *Ty* je třída, která má triviální operátor přiřazení přesunutí, jinak má hodnotu false.

Operátor přiřazení přesunu pro třídu *Ty* triviální pokud:

implicitně se poskytuje

Třída *Ty* nemá žádné virtuální funkce

Třída *Ty* nemá žádné virtuálních základních tříd

třídy všechny nestatické datové členy typu třídy mají operátory přiřazení pro přesunutí jednoduchého dotazu

třídy nestatických datových členů typu pole třídy mají operátory přiřazení pro přesunutí jednoduchého dotazu

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>

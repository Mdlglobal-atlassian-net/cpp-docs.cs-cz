---
title: is_trivially_move_assignable – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_move_assignable
helpviewer_keywords:
- is_trivially_move_assignable
ms.assetid: 374f7322-0706-4bc1-a1a5-4191d0315e28
ms.openlocfilehash: 324e4a1f1bd3528f09f21c5e485ac814038b7517
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448372"
---
# <a name="istriviallymoveassignable-class"></a>is_trivially_move_assignable – třída

Testuje, zda má typ operátor přiřazení triviálního přesunutí.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_trivially_move_assignable;
```

### <a name="parameters"></a>Parametry

*Ty*\
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Instance predikátu typu má hodnotu true, *Pokud typ je* třída, která má operátor přiřazení triviálního přesunu, jinak obsahuje hodnotu false.

Operátor přiřazení přesunu pro *danou třídu je* triviální, pokud:

implicitně se poskytuje

Třída *ty* nemá žádné virtuální funkce.

Třída *ty* nemá žádné virtuální základy.

třídy všech nestatických datových členů typu třídy mají operátory přiřazení triviálního přesunutí.

třídy všech nestatických datových členů typu Array třídy mají operátory přiřazení triviálního přesunutí.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)

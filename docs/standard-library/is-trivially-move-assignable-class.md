---
title: is_trivially_move_assignable – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_move_assignable
helpviewer_keywords:
- is_trivially_move_assignable
ms.assetid: 374f7322-0706-4bc1-a1a5-4191d0315e28
ms.openlocfilehash: 4b349d328da995105a6217f4ab597da5d7eafc38
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689494"
---
# <a name="is_trivially_move_assignable-class"></a>is_trivially_move_assignable – třída

Testuje, zda má typ operátor přiřazení triviálního přesunutí.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_trivially_move_assignable;
```

### <a name="parameters"></a>Parametry

*Ty* \
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Instance predikátu typu má hodnotu true, *Pokud typ je* třída, která má operátor přiřazení triviálního přesunu, jinak obsahuje hodnotu false.

Operátor přiřazení přesunu pro *danou třídu je* triviální, pokud:

- implicitně se poskytuje
- Třída *ty* nemá žádné virtuální funkce.
- Třída *ty* nemá žádné virtuální základy.
- třídy všech nestatických datových členů typu třídy mají operátory přiřazení triviálního přesunutí.
- třídy všech nestatických datových členů typu Array třídy mají operátory přiřazení triviálního přesunutí.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)

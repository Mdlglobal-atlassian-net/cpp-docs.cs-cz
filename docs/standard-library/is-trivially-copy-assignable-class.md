---
title: is_trivially_copy_assignable Class
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_copy_assignable
helpviewer_keywords:
- is_trivially_copy_assignable
ms.assetid: 7410133e-f367-493f-92a7-e34e3ec5e879
ms.openlocfilehash: c0019257a032d3becc268513336ed59e58a2e1d5
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447999"
---
# <a name="istriviallycopyassignable-class"></a>is_trivially_copy_assignable Class

Testuje, zda má typ operátor přiřazení triviální kopie.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_trivially_copy_assignable;
```

### <a name="parameters"></a>Parametry

*Š*\
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Instance predikátu typu má hodnotu true, pokud typ *T* je třída, která má operátor přiřazení triviální kopie, v opačném případě obsahuje hodnotu false.

Konstruktor přiřazení pro třídu *t* je triviální, pokud je implicitně poskytnutý, třída *t* nemá žádné virtuální funkce, třída *t* nemá žádné virtuální základy, třídy všech nestatických datových členů typu třídy mají triviální přiřazení. operátory a třídy všech nestatických datových členů typu Array třídy mají operátory přiřazení triviální.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)

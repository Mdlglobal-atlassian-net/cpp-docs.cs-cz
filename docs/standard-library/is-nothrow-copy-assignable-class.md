---
title: is_nothrow_copy_assignable – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_copy_assignable
helpviewer_keywords:
- is_nothrow_copy_assignable
ms.assetid: baa8abd6-4f53-489f-abba-8d5d5c53bbbc
ms.openlocfilehash: 330c97cd945e161d2bf47deb377dd732bf53b3c9
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455980"
---
# <a name="isnothrowcopyassignable-class"></a>is_nothrow_copy_assignable – třída

Testuje, zda typ obsahuje operátor přiřazení kopie, který je znám pro kompilátor, který nemá být vyvolána.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_nothrow_copy_assignable;
```

### <a name="parameters"></a>Parametry

*Š*\
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Instance predikátu typu má hodnotu true pro odkazující typ *T* , kde `is_nothrow_assignable<T&, const T&>` má hodnotu true. v opačném případě obsahuje hodnotu false.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[< type_traits >](../standard-library/type-traits.md)\
[is_nothrow_assignable – třída](../standard-library/is-nothrow-assignable-class.md)

---
title: is_copy_assignable Class
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_copy_assignable
helpviewer_keywords:
- is_copy_assignable
ms.assetid: 3ae6bca1-85fb-4829-9ee9-0183b081ff50
ms.openlocfilehash: 5fedd32f026828e49ea29cb2975a2529ca28c862
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452830"
---
# <a name="iscopyassignable-class"></a>is_copy_assignable Class

Testuje, zda je možné kopírovat typ při přiřazení.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_copy_assignable;
```

### <a name="parameters"></a>Parametry

*Ty*\
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Instance predikátu typu má hodnotu true, *Pokud typ je* třída, která má operátor přiřazení kopie, v opačném případě obsahuje hodnotu false. Ekvivalentem is_assignable\<&, const Ty & >.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)

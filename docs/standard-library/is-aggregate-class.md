---
title: is_aggregate – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_aggregate
helpviewer_keywords:
- is_aggregate
ms.openlocfilehash: 89749e2b4c0e6aaf00de074718cfb598333bc739
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456692"
---
# <a name="isaggregate-class"></a>is_aggregate – třída

Testuje, zda je typ typu třídy označeno `aggregate`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_aggregate;
```

### <a name="parameters"></a>Parametry

*Š*\
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Instance predikátu typu má hodnotu true, pokud typ *T* je typ třídy označený jako `aggregate`, jinak obsahuje hodnotu false. Pokud *T* je typ třídy, musí být úplný typ.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)

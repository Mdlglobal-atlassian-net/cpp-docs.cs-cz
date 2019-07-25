---
title: is_lvalue_reference – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_lvalue_reference
helpviewer_keywords:
- is_lvalue_reference class
- is_lvalue_reference
ms.assetid: 7f11896b-935c-4de1-9c87-9d0127f904e2
ms.openlocfilehash: 5bcd5c8333f011475cb11a452759c8986ab22215
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456205"
---
# <a name="islvaluereference-class"></a>is_lvalue_reference – třída

Testuje, zda je typ odkaz l-hodnota.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_lvalue_reference;
```

### <a name="parameters"></a>Parametry

*Ty*\
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Instance tohoto predikátu typu má hodnotu true, pokud je *typ,* který je odkazem na objekt nebo funkci, jinak obsahuje hodnotu false. Upozorňujeme, že *ty* nemusí být odkaz rvalue. Další informace o rvalue naleznete v tématu [rvalue reference deklarátor: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="requirements"></a>Požadavky

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[< type_traits >](../standard-library/type-traits.md)\
[L-hodnoty a r-hodnoty](../cpp/lvalues-and-rvalues-visual-cpp.md)

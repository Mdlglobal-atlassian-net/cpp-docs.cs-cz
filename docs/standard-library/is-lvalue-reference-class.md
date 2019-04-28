---
title: is_lvalue_reference – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_lvalue_reference
helpviewer_keywords:
- is_lvalue_reference class
- is_lvalue_reference
ms.assetid: 7f11896b-935c-4de1-9c87-9d0127f904e2
ms.openlocfilehash: e032522e790b7027886ba1a6199ed7fdf86c0936
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351940"
---
# <a name="islvaluereference-class"></a>is_lvalue_reference – třída

Testuje, zda je typ reference na lvalue.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_lvalue_reference;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Instance této predikátu typu obsahuje hodnotu true, pokud typ *Ty* je odkaz na objekt nebo na funkci; v opačném případě obsahuje hodnotu false. Všimněte si, že *Ty* nemusí být odkaz rvalue. Další informace o hodnotách rvalue naleznete v tématu [Rvalue Reference Declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
[L-hodnoty a r-hodnoty](../cpp/lvalues-and-rvalues-visual-cpp.md)<br/>

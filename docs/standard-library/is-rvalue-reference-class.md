---
title: is_rvalue_reference – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_rvalue_reference
helpviewer_keywords:
- is_rvalue_reference class
- is_rvalue_reference
ms.assetid: 40a97072-7b5c-4274-9154-298d3dcf064a
ms.openlocfilehash: ea3be02db2a4a840ed8f8b8a253d7409c26cf759
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604127"
---
# <a name="isrvaluereference-class"></a>is_rvalue_reference – třída

Testuje, zda je typ odkaz rvalue.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_rvalue_reference;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Instance této predikátu typu obsahuje hodnotu true, pokud typ *Ty* je [odkaz rvalue](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
[Hodnoty lvalue a rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md)<br/>

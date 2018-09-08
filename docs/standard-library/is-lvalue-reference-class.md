---
title: is_lvalue_reference – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_lvalue_reference
dev_langs:
- C++
helpviewer_keywords:
- is_lvalue_reference class
- is_lvalue_reference
ms.assetid: 7f11896b-935c-4de1-9c87-9d0127f904e2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ecd065ff80b5c45bca863534e28bc467b3a4105c
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44105377"
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
[Hodnoty lvalue a rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md)<br/>

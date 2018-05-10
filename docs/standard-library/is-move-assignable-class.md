---
title: is_move_assignable třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_move_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_move_assignable
ms.assetid: f33137f2-0639-4912-8745-bc0f9fd18d28
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: adda28e4c6cc2a7ba7a387e125bd873b2107b687
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="ismoveassignable-class"></a>is_move_assignable – třída

Testy, pokud typ lze přesunout přiřazené.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_move_assignable;
```

### <a name="parameters"></a>Parametry

`T` Typ k dotazu.

## <a name="remarks"></a>Poznámky

Typ je přesunout přiřadit, pokud lze přiřadit deklarátor odkazu na typ odkaz na typ. Je ekvivalentní predikátem typu `is_assignable<T&, T&&>`. Přesuňte typy Přiřaditelné obsahují kde Skalární typy a typy tříd, které mají generované kompilátorem nebo uživatelsky definovaných přesunout operátory přiřazení.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[<type_traits>](../standard-library/type-traits.md)<br/>

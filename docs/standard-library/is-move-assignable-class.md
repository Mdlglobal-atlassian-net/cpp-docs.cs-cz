---
title: is_move_assignable – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 3af5cbeae84b5b582077f543a39cfe408575bc71
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38960053"
---
# <a name="ismoveassignable-class"></a>is_move_assignable – třída

Testuje, zda může být typu přesuňte přiřazené.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_move_assignable;
```

### <a name="parameters"></a>Parametry

*T* typ dotazu.

## <a name="remarks"></a>Poznámky

Typ je přiřaditelný přesunout, pokud odkaz rvalue na typ, je možné přiřadit na odkaz na typ. Predikát typu je ekvivalentní `is_assignable<T&, T&&>`. Přesuňte přiřadit typy zahrnují označím Skalární typy a typy tříd, které se mají generované kompilátorem nebo uživatelem definované operátory přiřazení přesunutí.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>

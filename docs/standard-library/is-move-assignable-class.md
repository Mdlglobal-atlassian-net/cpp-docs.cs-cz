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
ms.openlocfilehash: 12647c6f2243b0804343f0485737a28c79afc6f0
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44100232"
---
# <a name="ismoveassignable-class"></a>is_move_assignable – třída

Testuje, zda může být typu přesuňte přiřazené.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_move_assignable;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Typ je přiřaditelný přesunout, pokud odkaz rvalue na typ, je možné přiřadit na odkaz na typ. Predikát typu je ekvivalentní `is_assignable<T&, T&&>`. Přesuňte přiřadit typy zahrnují označím Skalární typy a typy tříd, které se mají generované kompilátorem nebo uživatelem definované operátory přiřazení přesunutí.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>

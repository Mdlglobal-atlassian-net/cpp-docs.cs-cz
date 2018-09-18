---
title: Chyba kompilátoru C3530 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3530
dev_langs:
- C++
helpviewer_keywords:
- C3530
ms.assetid: 21be81ce-b699-4c74-81bc-80a0c34d2d5a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5866e2ea44b84f3afeb0cef8423abc28f8e056ab
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094790"
---
# <a name="compiler-error-c3530"></a>Chyba kompilátoru C3530

'auto' nelze kombinovat s jakékoli jiným specifikátorem typu.

Použití specifikátoru typu s `auto` – klíčové slovo.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Nepoužívejte specifikátor typu v deklaraci proměnné, která používá `auto` – klíčové slovo.

## <a name="example"></a>Příklad

Následující příklad provede C3530, protože proměnná `x` je deklarován s oběma `auto` – klíčové slovo a typ `int`, a protože příklad je zkompilován s **/Zc: Auto**.

```
// C3530.cpp
// Compile with /Zc:auto
int main()
{
   auto int x;   // C3530
   return 0;
}
```

## <a name="see-also"></a>Viz také

[Auto – klíčové slovo](../../cpp/auto-keyword.md)
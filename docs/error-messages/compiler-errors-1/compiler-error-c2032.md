---
title: Chyba kompilátoru C2032 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2032
dev_langs:
- C++
helpviewer_keywords:
- C2032
ms.assetid: 625d7c83-70b6-42c2-a558-81fbc0026324
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ab02ca695ec94f25054e3490232b782a46a53a4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46064006"
---
# <a name="compiler-error-c2032"></a>Chyba kompilátoru C2032

'identifier': funkce nemůže být členem struktury nebo sjednocení "structorunion.

Struktura nebo sjednocení má členská funkce, který je povolen v jazyce C++, ale ne v C. Chcete-li vyřešit chybu, zkompiluje kód jako programu v jazyce C++ nebo odeberte členskou funkci.

Následující ukázka generuje C2032:

```
// C2032.c
struct z {
   int i;
   void func();   // C2032
};
```

Možná řešení:

```
// C2032b.c
// compile with: /c
struct z {
   int i;
};
```
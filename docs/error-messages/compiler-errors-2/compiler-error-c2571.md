---
title: Chyba kompilátoru C2571 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2571
dev_langs:
- C++
helpviewer_keywords:
- C2571
ms.assetid: c6522616-dee9-4d7d-9bf8-30a7e1deaadf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 30cc078251d0511da77e08690db275a788973ffb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067932"
---
# <a name="compiler-error-c2571"></a>Chyba kompilátoru C2571

'function': virtuální funkce nemůže být sjednocení "sjednocení.

Sjednocení je deklarován s virtuální funkcí. Je možné deklarovat pouze ve třídě nebo struktuře virtuální funkce.  Možná řešení:

1. Změňte sjednocení na třídu nebo strukturu.

1. Ujistěte se, funkce nevirtuální.

Následující ukázka generuje C2571:

```
// C2571.cpp
// compile with: /c
union A {
   virtual void func1();   // C2571
   void func2();   // OK
};
```
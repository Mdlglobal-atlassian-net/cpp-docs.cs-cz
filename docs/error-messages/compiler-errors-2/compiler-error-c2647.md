---
title: Chyba kompilátoru C2647 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2647
dev_langs:
- C++
helpviewer_keywords:
- C2647
ms.assetid: 1034589e-bc3e-41a6-831f-2a1a4b8a2500
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 14187f7b74096a3a863798053ab260177d2f378b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045884"
---
# <a name="compiler-error-c2647"></a>Chyba kompilátoru C2647

'operator': Nelze přistoupit přes ukazatel 'type1' na 'type2'

Levý operand operátoru pointer-to-member ( `->*` nebo `.*` ) nejde implicitně převést na typ související s správný operátor.

Následující ukázka generuje C2647:

```
// C2647.cpp
class C {};
class D {};

int main() {
   D d, *pd;
   C c, *pc = 0;
   int C::*pmc = 0;
   pd->*pmc = 0;   // C2647
   d.*pmc = 0;   // C2647

   // OK
   pc->*pmc = 0;
   c.*pmc = 0;
}
```
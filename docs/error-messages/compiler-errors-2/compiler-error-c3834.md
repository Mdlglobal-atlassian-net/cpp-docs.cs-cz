---
title: Chyba kompilátoru C3834
ms.date: 11/04/2016
f1_keywords:
- C3834
helpviewer_keywords:
- C3834
ms.assetid: 059e0dc4-300b-4e74-b6c2-41a57831fe2a
ms.openlocfilehash: 9f2bb96beaac8ede75863084c8ebf8345c940f53
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50564161"
---
# <a name="compiler-error-c3834"></a>Chyba kompilátoru C3834

Neplatné explicitní přetypování na ukazatel Připnutí; Místo toho použijte připojenou lokální proměnnou

Explicitní přetypování na ukazatel na připojené nejsou povoleny.

## <a name="example"></a>Příklad

Následující ukázka generuje C3834.

```
// C3834.cpp
// compile with: /clr
int main() {
   int x = 33;

   pin_ptr<int> p = safe_cast<pin_ptr<int> >(&x);   // C3834
   pin_ptr<int> p2 = &x;   // OK
}
```

---
title: Chyba kompilátoru C3834
ms.date: 11/04/2016
f1_keywords:
- C3834
helpviewer_keywords:
- C3834
ms.assetid: 059e0dc4-300b-4e74-b6c2-41a57831fe2a
ms.openlocfilehash: 9f2bb96beaac8ede75863084c8ebf8345c940f53
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62327506"
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

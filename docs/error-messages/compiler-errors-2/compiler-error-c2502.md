---
title: Chyba kompilátoru C2502
ms.date: 11/04/2016
f1_keywords:
- C2502
helpviewer_keywords:
- C2502
ms.assetid: affa0b86-15fc-4e17-b7f2-6aad4a3771c4
ms.openlocfilehash: e23ccae55c40c9652f5a3e1f55c834a968bca784
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50601605"
---
# <a name="compiler-error-c2502"></a>Chyba kompilátoru C2502

'identifier': moc velký počet modifikátorů přístupu základní třídy

Základní třída má více než jeden modifikátor přístupu. Modifikátor přístupu pouze jeden (`public`, `private`, nebo `protected`) je povolený.

Následující ukázka generuje C2502:

```
// C2502.cpp
// compile with: /c
class A { };
class B { };
class C : private public A { };   // C2502

// OK
class D : private A {};
class E : public A, private B {};
```
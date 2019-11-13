---
title: Upozornění kompilátoru (úroveň 3) C4310
ms.date: 11/04/2016
f1_keywords:
- C4310
helpviewer_keywords:
- C4310
ms.assetid: cba3eca1-f1ed-499c-9243-337446bdbdd8
ms.openlocfilehash: e4232c2c7b1d1caa918edb25d69015441b9c576d
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051649"
---
# <a name="compiler-warning-level-3-c4310"></a>Upozornění kompilátoru (úroveň 3) C4310

přetypování zkrátí konstantní hodnotu.

Konstantní hodnota je převedena na menší typ. Kompilátor provede přetypování, které zkrátí data. Následující ukázka generuje C4310:

```cpp
// C4310.cpp
// compile with: /W4
int main() {
   long int a;
   a = (char) 128;   // C4310, use value 0-127 to resolve
}
```
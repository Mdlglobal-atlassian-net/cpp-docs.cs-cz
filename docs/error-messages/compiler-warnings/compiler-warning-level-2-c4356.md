---
title: Upozornění (úroveň 2) C4356 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4356
dev_langs:
- C++
helpviewer_keywords:
- C4356
ms.assetid: 3af3defe-de33-43b6-bd6c-2c2e09e34f3f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 463ecd1bdd41c07baab0cf90c978411e51b4be04
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118723"
---
# <a name="compiler-warning-level-2-c4356"></a>Kompilátor upozornění (úroveň 2) C4356

'member': Statický datový člen nejde inicializovat prostřednictvím odvozené třídy

Inicializace statický datový člen byl chybně vytvořen. Kompilátor přijaté inicializace. Aby se zabránilo upozornění, inicializujte člena prostřednictvím základní třídy.

Použití [upozornění](../../preprocessor/warning.md) – Direktiva pragma pro potlačení tohoto upozornění.

Následující ukázka generuje C4356:

```
// C4356.cpp
// compile with: /W2 /EHsc
#include <iostream>

template <class T>
class C {
   static int n;
};

class D : C<int> {};

int D::n = 0; // C4356
// try the following line instead
// int C<int>::n = 0;

class A {
public:
   static int n;
};

class B : public A {};

int B::n = 10;   // C4356
// try the following line instead
// int A::n = 99;

int main() {
   using namespace std;
   cout << B::n << endl;
}
```
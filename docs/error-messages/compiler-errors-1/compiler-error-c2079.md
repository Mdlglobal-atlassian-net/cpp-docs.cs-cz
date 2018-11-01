---
title: Chyba kompilátoru C2079
ms.date: 11/04/2016
f1_keywords:
- C2079
helpviewer_keywords:
- C2079
ms.assetid: ca58d6d5-eccd-40b7-ba14-c003223c5bc7
ms.openlocfilehash: 68435610680e3b21415a1d9439a8133fd1e2557f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50621660"
---
# <a name="compiler-error-c2079"></a>Chyba kompilátoru C2079

'identifier' používá nedefinovanou třídu/strukturu/sjednocení "name"

Zadaný identifikátor je Nedefinovaná třída, struktura nebo sjednocení.

Tuto chybu může způsobovat anonymní sjednocení inicializace.

Následující ukázka generuje C2079:

```
// C2079.cpp
// compile with: /EHsc
#include <iostream>
int main() {
   std::ifstream g;   // C2079
}
```

Možná řešení:

```
// C2079b.cpp
// compile with: /EHsc
#include <fstream>
int main( ) {
   std::ifstream g;
}
```

C2079 může také dojít, pokud při pokusu o deklarovat objekt v zásobníku typu, jehož dopředné deklarace je jenom v oboru.

```
// C2079c.cpp
class A;

class B {
   A a;   // C2079
};

class A {};
```

Možná řešení:

```
// C2079d.cpp
// compile with: /c
class A;
class C {};

class B {
   A * a;
   C c;
};

class A {};
```
---
title: Chyba kompilátoru C2079
ms.date: 11/04/2016
f1_keywords:
- C2079
helpviewer_keywords:
- C2079
ms.assetid: ca58d6d5-eccd-40b7-ba14-c003223c5bc7
ms.openlocfilehash: 68435610680e3b21415a1d9439a8133fd1e2557f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391956"
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
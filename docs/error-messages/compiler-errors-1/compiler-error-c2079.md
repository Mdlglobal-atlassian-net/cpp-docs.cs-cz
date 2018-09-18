---
title: Chyba kompilátoru C2079 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2079
dev_langs:
- C++
helpviewer_keywords:
- C2079
ms.assetid: ca58d6d5-eccd-40b7-ba14-c003223c5bc7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9ddea9a8651a62f7cbb857e1d53962142471c2cb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032175"
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
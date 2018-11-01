---
title: Chyba kompilátoru C2249
ms.date: 11/04/2016
f1_keywords:
- C2249
helpviewer_keywords:
- C2249
ms.assetid: bdd6697c-e04b-49b9-8e40-d9eb6d74f2b6
ms.openlocfilehash: f3f82549cf5d9230adfee7e83248e92f8e93e769
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555624"
---
# <a name="compiler-error-c2249"></a>Chyba kompilátoru C2249

'member': není dostupná žádná cesta pro přístup k členu deklarované v virtuální base 'class'

`member` Je zděděno od nonpublic `virtual` základní třídy nebo struktury.

## <a name="example"></a>Příklad

Následující ukázka generuje C2249.

```
// C2249.cpp
class A {
private:
   void privFunc( void ) {};
public:
   void pubFunc( void ) {};
};

class B : virtual public A {} b;

int main() {
   b.privFunc();    // C2249, private member of A
   b.pubFunc();    // OK
}
```

## <a name="example"></a>Příklad

C2249 může také dojít, pokud se pokusíte přiřadit datového proudu ze standardní knihovny C++ do jiného datového proudu.  Následující ukázka generuje C2249.

```
// C2249_2.cpp
#include <iostream>
using namespace std;
int main() {
   cout = cerr;   // C2249
   #define cout cerr;   // OK
}
```
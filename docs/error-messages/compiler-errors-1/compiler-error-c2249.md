---
title: Chyba kompilátoru C2249 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2249
dev_langs:
- C++
helpviewer_keywords:
- C2249
ms.assetid: bdd6697c-e04b-49b9-8e40-d9eb6d74f2b6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cb9c73ca311b767d9fdb50dd55a832cf8fcc2a4b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46089889"
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
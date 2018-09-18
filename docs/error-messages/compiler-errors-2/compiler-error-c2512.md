---
title: Chyba kompilátoru C2512 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/09/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2512
dev_langs:
- C++
helpviewer_keywords:
- C2512
ms.assetid: 15206da9-1164-451a-b869-280e00711aad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ba1fbba98237879927fd82d6535c0c2688c1c304
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036915"
---
# <a name="compiler-error-c2512"></a>Chyba kompilátoru C2512

> "*identifikátor*': žádný odpovídající konstruktor default k dispozici

A *výchozí konstruktor*, konstruktor, který nevyžaduje argumenty, není k dispozici pro zadanou třídu, strukturu nebo sjednocení. Pouze v případě, že jsou k dispozici žádné uživatelem definované konstruktory, kompilátor poskytuje výchozí konstruktor.

Pokud zadáte konstruktor, který přijímá parametr typ jiný než void a budete chtít povolit vaší třídy, který bude vytvořen bez parametrů (například jako prvky pole), musíte taky zadat výchozí konstruktor. Výchozí konstruktor může být konstruktor s použitím výchozích hodnot pro všechny parametry.

## <a name="example"></a>Příklad

Běžnou příčinou chyby C2512 je při definování třídy nebo struktury konstruktor, který přebírá argumenty a potom se pokusíte o deklaraci instance třídy nebo struktury bez argumentů. Například `struct B` níže deklaruje konstruktor, který vyžaduje `char *` argument, ale ne ten, který nepřijímá žádné argumenty. V `main`, je deklarována instance b, ale není zadaný žádný argument. Kompilátor generuje C2512, protože nelze najít výchozí konstruktor pro služby serveru B.

```cpp
// C2512.cpp
// Compile with: cl /W4 c2512.cpp
// C2512 expected
struct B {
   B (char *) {}
   // Uncomment the following line to fix.
   // B() {}
};

int main() {
   B b;   // C2512 - This requires a default constructor
}
```

Tento problém můžete opravit tak, že definujete výchozí konstruktor pro struktury nebo třídy, jako například `B() {}`, nebo pokud všechny argumenty mají výchozí hodnoty, jako například konstruktor `B (char * = nullptr) {}`.

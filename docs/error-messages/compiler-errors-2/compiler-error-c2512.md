---
title: "C2512 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 02/09/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2512
dev_langs:
- C++
helpviewer_keywords:
- C2512
ms.assetid: 15206da9-1164-451a-b869-280e00711aad
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 57dbb542eee7e893253e6c3bdd3410c605a8d2db
ms.sourcegitcommit: 8ae12a602244a5853e941e5e8806e3545d876844
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2018
---
# <a name="compiler-error-c2512"></a>C2512 chyby kompilátoru

> '*identifikátor*': žádný odpovídající výchozí konstruktor k dispozici  

A *výchozí konstruktor*, není k dispozici pro určité třídy, struktury nebo sjednocení konstruktor, který vyžaduje žádné argumenty. Kompilátor poskytuje výchozí konstruktor pouze v případě, že jsou k dispozici žádné uživatelem definované konstruktory.

Pokud zadáte konstruktor, který přebírá parametr není void a chcete povolit vlastní třídy, který bude vytvořen bez parametrů (například jako elementy pole), je nutné také zadat výchozí konstruktor. Výchozí konstruktor může být konstruktor se výchozí hodnoty pro všechny parametry.

## <a name="example"></a>Příklad

Obvyklou příčinou chyby C2512 je při definování třídě nebo struktuře konstruktor, který přebírá argumenty a poté pokusíte deklarujte instanci vaší třídě nebo struktuře bez argumentů. Například `struct B` níže deklaruje konstruktor, který vyžaduje `char *` argument, ale není jednou, který nemá žádné argumenty. V `main`, deklarována instance B, ale nebude zadán žádný argument. Kompilátor generuje C2512, protože nelze nalézt výchozí konstruktor pro B.

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

Tento problém můžete vyřešit tak, že definujete výchozí konstruktor pro třídy, nebo struktury, jako `B() {}`, nebo konstruktor, kde všechny argumenty mají výchozí hodnoty, jako například `B (char * = nullptr) {}`.

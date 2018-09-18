---
title: Upozornění (úroveň 3) C4522 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4522
dev_langs:
- C++
helpviewer_keywords:
- C4522
ms.assetid: 7065dc27-0b6c-4e68-a345-c51cdb99a20b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 65662d3e62abbeb06127c7b5a49479a23fb20a7a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070935"
---
# <a name="compiler-warning-level-3-c4522"></a>Kompilátor upozornění (úroveň 3) C4522

'class': zadaných víc operátorů přiřazení

Třída má víc operátorů přiřazení jednoho typu. Toto upozornění je informační; konstruktory jsou volány v programu.

Použití [upozornění](../../preprocessor/warning.md) – Direktiva pragma pro potlačení tohoto upozornění.

## <a name="example"></a>Příklad

Následující ukázka generuje C4522.

```
// C4522.cpp
// compile with: /EHsc /W3
#include <iostream>

using namespace std;
class A {
public:
   A& operator=( A & o ) { cout << "A&" << endl; return *this; }
   A& operator=( const A &co ) { cout << "const A&" << endl; return *this; }   // C4522
};

int main() {
   A o1, o2;
   o2 = o1;
   const A o3;
   o1 = o3;
}
```
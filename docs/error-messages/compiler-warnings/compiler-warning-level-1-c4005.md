---
title: Kompilátor upozornění (úroveň 1) C4005
ms.date: 11/04/2016
f1_keywords:
- C4005
helpviewer_keywords:
- C4005
ms.assetid: 7f2dc79a-9fcb-4d5b-be61-120d9cb487ad
ms.openlocfilehash: 76aab2160bd5f7918771dcf63b7297a869da751e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651292"
---
# <a name="compiler-warning-level-1-c4005"></a>Kompilátor upozornění (úroveň 1) C4005

'identifier': předefinování makra

Identifikátor – makro je definována dvakrát. Kompilátor používá druhou definici makra.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit tak, že zkontrolujete následující možné příčiny

1. Definování makra na příkazovém řádku a v kódu adresou `#define` směrnice.

1. Makra naimportované z vložených souborů.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li vyřešit pomocí následujících možná řešení

1. Odeberte jednu z definic.

1. Použití [#undef](../../preprocessor/hash-undef-directive-c-cpp.md) direktiv před druhá definice.

Následující ukázka generuje C4005:

```
// C4005.cpp
// compile with: /W1 /EHsc
#include <iostream>
using namespace std;

#define TEST "test1"
#define TEST "test2"   // C4005 delete or rename to resolve the warning

int main() {
   cout << TEST << endl;
}
```
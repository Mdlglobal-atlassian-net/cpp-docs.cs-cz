---
title: Upozornění kompilátoru (úroveň 1) C4005
ms.date: 11/04/2016
f1_keywords:
- C4005
helpviewer_keywords:
- C4005
ms.assetid: 7f2dc79a-9fcb-4d5b-be61-120d9cb487ad
ms.openlocfilehash: 71b23ec719198d15a99b4fcfd50db8b151e03226
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627359"
---
# <a name="compiler-warning-level-1-c4005"></a>Upozornění kompilátoru (úroveň 1) C4005

' identifier ': předefinování makra

Identifikátor makra je definován dvakrát. Kompilátor používá druhou definici makra.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Opravu provedete kontrolou následujících možných příčin.

1. Definování makra na příkazovém řádku a v kódu s direktivou `#define`.

1. Makra importovaná ze souborů k zahrnutí

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Oprava pomocí následujících možných řešení

1. Odeberte jednu z definic.

1. Před druhou definicí Použijte direktivu [#undef](../../preprocessor/hash-undef-directive-c-cpp.md) .

Následující ukázka generuje C4005:

```cpp
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
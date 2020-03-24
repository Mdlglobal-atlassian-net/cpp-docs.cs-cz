---
title: Upozornění kompilátoru (úroveň 1) C4005
ms.date: 11/04/2016
f1_keywords:
- C4005
helpviewer_keywords:
- C4005
ms.assetid: 7f2dc79a-9fcb-4d5b-be61-120d9cb487ad
ms.openlocfilehash: 4e95f8deeb61c5a4d56e0643beb6a746f848e33e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164726"
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

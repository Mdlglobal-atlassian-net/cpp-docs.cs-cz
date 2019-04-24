---
title: Upozornění kompilátoru C4972
ms.date: 11/04/2016
f1_keywords:
- C4972
helpviewer_keywords:
- C4972
ms.assetid: d18e8e65-b2ef-4d75-a207-fbd0c17c9060
ms.openlocfilehash: 7c58258298fb91d04014e719732135a1f33f13b6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62280695"
---
# <a name="compiler-warning-c4972"></a>Upozornění kompilátoru C4972

Přímá úprava nebo zpracování výsledku operace unbox jako l-hodnota se nelze ověřit

Přesměrování popisovače na typ hodnoty, označované také jako rozbalení a přiřazením k němu není možné ověřit.

Další informace najdete v tématu [zabalení](../../extensions/boxing-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C4972.

```
// C4972.cpp
// compile with: /clr:safe
using namespace System;
ref struct R {
   int ^ p;   // a value type
};

int main() {
   R ^ r = gcnew R;
   *(r->p) = 10;   // C4972

   // OK
   r->p = 10;
   Console::WriteLine( r->p );
   Console::WriteLine( *(r->p) );
}
```
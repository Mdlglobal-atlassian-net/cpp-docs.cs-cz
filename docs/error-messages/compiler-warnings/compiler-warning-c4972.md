---
title: Upozornění kompilátoru C4972 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4972
dev_langs:
- C++
helpviewer_keywords:
- C4972
ms.assetid: d18e8e65-b2ef-4d75-a207-fbd0c17c9060
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e083a91397ee00d8e74b5ee4549a192bba62b643
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037772"
---
# <a name="compiler-warning-c4972"></a>Upozornění kompilátoru C4972

Přímá úprava nebo zpracování výsledku operace unbox jako l-hodnota se nelze ověřit

Přesměrování popisovače na typ hodnoty, označované také jako rozbalení a přiřazením k němu není možné ověřit.

Další informace najdete v tématu [zabalení](../../windows/boxing-cpp-component-extensions.md).

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
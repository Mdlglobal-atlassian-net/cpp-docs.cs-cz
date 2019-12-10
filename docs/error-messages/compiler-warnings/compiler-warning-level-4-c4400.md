---
title: Upozornění kompilátoru (úroveň 4) C4400
ms.date: 11/04/2016
f1_keywords:
- C4400
helpviewer_keywords:
- C4400
ms.assetid: f135fe98-4f92-4e07-9d71-2621b36ee755
ms.openlocfilehash: 3f04bd30c4d390cecfa7e4e636f1a3771f26cfff
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990846"
---
# <a name="compiler-warning-level-4-c4400"></a>Upozornění kompilátoru (úroveň 4) C4400

Typ: kvalifikátory const/volatile pro tento typ nejsou podporované.

Kvalifikátory [const](../../cpp/const-cpp.md)a [volatile](../../cpp/volatile-cpp.md)nebudou fungovat s proměnnými typů modulu CLR (Common Language Runtime).

## <a name="example"></a>Příklad

Následující ukázka generuje C4400.

```cpp
// C4400.cpp
// compile with: /clr /W4
// C4401 expected
using namespace System;
#pragma warning (disable : 4101)
int main() {
   const String^ str;   // C4400
   volatile String^ str2;   // C4400
}
```

---
title: Chyba kompilátoru C3076
ms.date: 11/04/2016
f1_keywords:
- C3076
helpviewer_keywords:
- C3076
ms.assetid: 8a87b3e4-2c17-4b87-9622-ef0962d6a34e
ms.openlocfilehash: ac9afdfc11a13dd667b06289c73332593a4d884e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406649"
---
# <a name="compiler-error-c3076"></a>Chyba kompilátoru C3076

'instance': nemůžete vložit instanci typu odkazu, "typu", v nativním typu

Nativní typ nemůže obsahovat instanci typu CLR.

Další informace najdete v tématu [C++ – sémantika zásobníku pro odkazové typy](../../dotnet/cpp-stack-semantics-for-reference-types.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3076.

```
// C3076.cpp
// compile with: /clr /c
ref struct U {};

struct V {
   U y;   // C3076
};

ref struct W {
   U y;   // OK
};
```
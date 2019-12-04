---
title: Chyba kompilátoru C3063
ms.date: 11/04/2016
f1_keywords:
- C3063
helpviewer_keywords:
- C3063
ms.assetid: 0ecf6f1f-e4a7-487a-9fd5-79d8ac470001
ms.openlocfilehash: c52a0a4c4255eeed5f49a7e6c1e86a1f64b8ad77
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755652"
---
# <a name="compiler-error-c3063"></a>Chyba kompilátoru C3063

operátor operator: všechny operandy musí mít stejný typ výčtu.

Při použití operátorů u enumerátorů musí být oba operandy typu výčtu. Další informace naleznete v tématu [How to: Define and spotřebovávají výčty v C++/CLI](../../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3063 a ukazuje, jak ji opravit:

```cpp
// C3063.cpp
// compile with: /clr
enum class E { a, b } e, mask;
int main() {
   if ( ( e & mask ) != 0 ) ;   // C3063 no operator!= (E, int)

   if ( ( e & mask ) != E() )   // OK
      ;
}
```

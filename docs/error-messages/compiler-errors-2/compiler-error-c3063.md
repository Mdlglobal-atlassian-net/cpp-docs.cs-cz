---
title: Chyba kompilátoru C3063
ms.date: 11/04/2016
f1_keywords:
- C3063
helpviewer_keywords:
- C3063
ms.assetid: 0ecf6f1f-e4a7-487a-9fd5-79d8ac470001
ms.openlocfilehash: 9e53d9fe273a392695212df6dbeb679822a39068
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50485530"
---
# <a name="compiler-error-c3063"></a>Chyba kompilátoru C3063

operátor 'operator': všechny operandy musí mít stejný typ výčtu

Při použití operátorů na enumerátorech, oba operandy musí být typu výčtu. Další informace najdete v tématu [postupy: definice a používání výčtů v jazyce C + +/ CLI](../../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3063 a ukazuje, jak ho opravit:

```
// C3063.cpp
// compile with: /clr
enum class E { a, b } e, mask;
int main() {
   if ( ( e & mask ) != 0 ) ;   // C3063 no operator!= (E, int)

   if ( ( e & mask ) != E() )   // OK
      ;
}
```
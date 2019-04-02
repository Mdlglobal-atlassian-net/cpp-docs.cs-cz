---
title: Chyba kompilátoru C3071
ms.date: 11/04/2016
f1_keywords:
- C3071
helpviewer_keywords:
- C3071
ms.assetid: 69879e66-a60e-4058-9bbd-d5c5e2d8ee37
ms.openlocfilehash: 1debe431711681a98b9472c85864d84373ec42d6
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58775995"
---
# <a name="compiler-error-c3071"></a>Chyba kompilátoru C3071

operátor 'operator' může používat jedině pro instanci ref class nebo value-type.

Operátor CLR nelze použít v nativním typu. Operátor, který lze použít na třídy ref class nebo ref struct (typu hodnoty), ale nejsou nativní typ například int nebo alias pro nativní typ, jako je například System::Int32. Tyto typy nemůže být pevně určený z kódu jazyka C++ způsobem, který odkazuje na nativní proměnnou, takže se nedá použít operátor.

Další informace najdete v tématu [Tracking Reference Operator](../../extensions/tracking-reference-operator-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3071.

```
// C3071.cpp
// compile with: /clr
class N {};
ref struct R {};

int main() {
   N n;
   %n;   // C3071

   R r;
   R ^ r2 = %r;   // OK
}
```
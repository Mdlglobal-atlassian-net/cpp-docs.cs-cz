---
title: Chyba kompilátoru C3071 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3071
dev_langs:
- C++
helpviewer_keywords:
- C3071
ms.assetid: 69879e66-a60e-4058-9bbd-d5c5e2d8ee37
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5f004de3ed133ea77d543014ae1adcdc4e1eddef
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077799"
---
# <a name="compiler-error-c3071"></a>Chyba kompilátoru C3071

operátor 'operator' může používat jedině pro instanci ref class nebo value-type.

Operátor CLR nelze použít v nativním typu. Operátor, který lze použít na třídy ref class nebo ref struct (typu hodnoty), ale nejsou nativní typ například int nebo alias pro nativní typ, jako je například System::Int32. Tyto typy nemůže být pevně určený z kódu jazyka C++ způsobem, který odkazuje na nativní proměnnou, takže se nedá použít operátor.

Další informace najdete v tématu [Tracking Reference Operator](../../windows/tracking-reference-operator-cpp-component-extensions.md).

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
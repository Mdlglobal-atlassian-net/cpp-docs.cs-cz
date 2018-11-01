---
title: Chyba kompilátoru C3072
ms.date: 11/04/2016
f1_keywords:
- C3072
helpviewer_keywords:
- C3072
ms.assetid: cdd5cb6b-c478-4698-adfa-c40188d34a18
ms.openlocfilehash: 34b5cff9191814b2a16a42d9e234bab09f29c117
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490022"
---
# <a name="compiler-error-c3072"></a>Chyba kompilátoru C3072

operátor 'operator' nejde použít na instanci třídy ref class.

použít unární "`operator` ' operátor převodu instance třídy ref class na typ popisovače

Typ CLR vyžaduje operátory CLR, nikoli operátory nativní (nebo standard).  Další informace najdete v tématu [Tracking Reference Operator](../../windows/tracking-reference-operator-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3072.

```
// C3072.cpp
// compile with: /clr
ref class R {};

int main() {
   R r1;
   R^ r2 = &r1;   // C3072
   R^ r3 = %r1;   // OK
}
```
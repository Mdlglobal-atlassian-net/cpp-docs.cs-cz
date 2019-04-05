---
title: Chyba kompilátoru C3072
ms.date: 11/04/2016
f1_keywords:
- C3072
helpviewer_keywords:
- C3072
ms.assetid: cdd5cb6b-c478-4698-adfa-c40188d34a18
ms.openlocfilehash: 2b76fa91d739e9cc89251aaf56aa9b196e62a68d
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "58777126"
---
# <a name="compiler-error-c3072"></a>Chyba kompilátoru C3072

operátor 'operator' nejde použít na instanci třídy ref class.

použít unární "`operator` ' operátor převodu instance třídy ref class na typ popisovače

Typ CLR vyžaduje operátory CLR, nikoli operátory nativní (nebo standard).  Další informace najdete v tématu [Tracking Reference Operator](../../extensions/tracking-reference-operator-cpp-component-extensions.md).

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
---
title: Chyba kompilátoru C3181
ms.date: 11/04/2016
f1_keywords:
- C3181
helpviewer_keywords:
- C3181
ms.assetid: 5d450f8b-6cef-4452-a0c4-2076e967451d
ms.openlocfilehash: b37b28b4332b46aaaf803f58090a72c25e83f47f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587756"
---
# <a name="compiler-error-c3181"></a>Chyba kompilátoru C3181

'type': Neplatný operand pro: – operátor

Byl předán neplatný parametr [typeid](../../windows/typeid-cpp-component-extensions.md) operátor. Parametr musí být spravovaným typem.

Všimněte si, že kompilátor používá aliasy pro nativní typy, které jsou mapovány na typy v modulu common language runtime.

Následující ukázka generuje C3181:

```
// C3181a.cpp
// compile with: /clr
using namespace System;

int main() {
   Type ^pType1 = interior_ptr<int>::typeid;   // C3181
   Type ^pType2 = int::typeid;   // OK
}
```

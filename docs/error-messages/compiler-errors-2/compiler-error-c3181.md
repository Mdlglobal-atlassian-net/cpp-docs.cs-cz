---
title: Chyba kompilátoru C3181 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3181
dev_langs:
- C++
helpviewer_keywords:
- C3181
ms.assetid: 5d450f8b-6cef-4452-a0c4-2076e967451d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 599fe0afe4bdcdc7b1e2025859d11a38618b1349
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097338"
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

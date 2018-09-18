---
title: Upozornění kompilátoru C4950 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4950
dev_langs:
- C++
helpviewer_keywords:
- C4950
ms.assetid: 50226a5c-c664-4d09-ac59-e9e874ca244f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 750295da5d2da42ae4c2aac4fbb04dd208a7f32c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46072209"
---
# <a name="compiler-warning-c4950"></a>Upozornění kompilátoru C4950

'typ nebo člen': označené jako zastaralé

Člen nebo typ byl označený jako zastaralý s <xref:System.ObsoleteAttribute> atribut.

C4950 je vždy vyvoláno jako chyba. Toto upozornění můžete vypnout pomocí [upozornění](../../preprocessor/warning.md) – Direktiva pragma nebo [/wd](../../build/reference/compiler-option-warning-level.md) – možnost kompilátoru.

## <a name="example"></a>Příklad

Následující ukázka generuje C4950:

```cpp
// C4950.cpp
// compile with: /clr
using namespace System;

// Any reference to Func3 should generate an error with message
[System::ObsoleteAttribute("Will be removed in next version", true)]
Int32 Func3(Int32 a, Int32 b) {
   return (a + b);
}

int main() {
   Int32 MyInt3 = ::Func3(2, 2);   // C4950
}
```
---
title: Upozornění (úroveň 1) C4566 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4566
dev_langs:
- C++
helpviewer_keywords:
- C4566
ms.assetid: 65f40730-e86f-447c-b37b-16caadcfe311
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c25ff9d2a4c915570a28752d11778983f2cf2fc3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049173"
---
# <a name="compiler-warning-level-1-c4566"></a>Kompilátor upozornění (úroveň 1) C4566

znak reprezentován universal-character-name 'char' nemůže být reprezentovaný v aktuální znakové stránce (stránky)

Každý znak Unicode lze znázornit v aktuální znakové stránce ANSI.

Úzký řetězce (jeden bajtové znaků), jsou převedeny na vícebajtové znaky vzhledem k tomu jsou velké řetězce (dvoubajtové znaky) není.

Následující ukázka generuje C4566:

```
// C4566.cpp
// compile with: /W1
int main() {
   char c1 = '\u03a0';   // C4566
   char c2 = '\u0642';   // C4566

   wchar_t c3 = L'\u03a0';   // OK
   wchar_t c4 = L'\u0642';   // OK
}
```
---
title: Upozornění kompilátoru (úroveň 1) C4087
ms.date: 11/04/2016
f1_keywords:
- C4087
helpviewer_keywords:
- C4087
ms.assetid: 546e4d57-5c8e-422c-8ef1-92657336dad5
ms.openlocfilehash: d939edfdf00b81837a167ab326ab5a7791e3e374
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164011"
---
# <a name="compiler-warning-level-1-c4087"></a>Upozornění kompilátoru (úroveň 1) C4087

' function ': deklarováno se seznamem parametrů ' void '

Deklarace funkce nemá žádné formální parametry, ale volání funkce má skutečné parametry. Další parametry jsou předány podle konvence volání funkce.

Toto upozornění je pro kompilátor jazyka C.

## <a name="example"></a>Příklad

```c
// C4087.c
// compile with: /W1
int f1( void ) {
}

int main() {
   f1( 10 );   // C4087
}
```

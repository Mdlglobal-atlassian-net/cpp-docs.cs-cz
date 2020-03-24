---
title: Chyba kompilátoru C2094
ms.date: 11/04/2016
f1_keywords:
- C2094
helpviewer_keywords:
- C2094
ms.assetid: 9e4f8f88-f189-46e7-91c9-481bacc7af87
ms.openlocfilehash: 022fca01706fefca2a14ea952586ec91b0c5b240
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80207675"
---
# <a name="compiler-error-c2094"></a>Chyba kompilátoru C2094

Jmenovka ' identifikátor ' nebyla definována.

Popisek použitý příkazem [goto](../../cpp/goto-statement-cpp.md) ve funkci neexistuje.

## <a name="example"></a>Příklad

Následující ukázka generuje C2094:

```cpp
// C2094.c
int main() {
   goto test;
}   // C2094
```

Možné řešení:

```cpp
// C2094b.c
int main() {
   goto test;
   test:
   {
   }
}
```

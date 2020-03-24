---
title: Upozornění kompilátoru (úroveň 1 a úroveň 4) C4949
ms.date: 11/04/2016
f1_keywords:
- C4949
helpviewer_keywords:
- C4949
ms.assetid: 34f45a05-c115-49cb-9f67-0bd4f0735d9b
ms.openlocfilehash: 7ce8b3242def187e4b8b442f403f92f013a9ca6e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164778"
---
# <a name="compiler-warning-level-1-and-level-4-c4949"></a>Upozornění kompilátoru (úroveň 1 a úroveň 4) C4949

direktivy pragma managed a unmanaged mají smysl, jenom když se zkompiluje s možností/CLR [: Option].

Kompilátor ignoruje [spravované](../../preprocessor/managed-unmanaged.md) a nespravované direktivy pragma, pokud zdrojový kód není zkompilován s možností [/CLR](../../build/reference/clr-common-language-runtime-compilation.md). Toto upozornění je informativní.

Následující ukázka generuje C4949:

```cpp
// C4949.cpp
// compile with: /LD /W1
#pragma managed   // C4949
```

Když **#pragma nespravované** , je použit bez **/CLR**, C4949 je upozornění úrovně 4.

Následující ukázka generuje C4949:

```cpp
// C4949b.cpp
// compile with: /LD /W4
#pragma unmanaged   // C4949
```

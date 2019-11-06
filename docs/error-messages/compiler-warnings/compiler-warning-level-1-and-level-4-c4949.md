---
title: Upozornění kompilátoru (úroveň 1 a úroveň 4) C4949
ms.date: 11/04/2016
f1_keywords:
- C4949
helpviewer_keywords:
- C4949
ms.assetid: 34f45a05-c115-49cb-9f67-0bd4f0735d9b
ms.openlocfilehash: f2876813131271ebb2561f8ea7435bb96dc2ce17
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627413"
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
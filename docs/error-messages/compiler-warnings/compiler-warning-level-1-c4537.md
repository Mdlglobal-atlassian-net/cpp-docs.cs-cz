---
title: Upozornění kompilátoru (úroveň 1) C4537
ms.date: 08/27/2018
f1_keywords:
- C4537
helpviewer_keywords:
- C4537
ms.assetid: 9454493c-d419-475e-8f35-9c00233c9329
ms.openlocfilehash: 81058f153228d3d8fbf4097c140962d0cb9677e5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186358"
---
# <a name="compiler-warning-level-1-c4537"></a>Upozornění kompilátoru (úroveň 1) C4537

> '*Object*': '*operátor*' použit pro typ, který není typu UDT

## <a name="remarks"></a>Poznámky

Byl předán odkaz na místo, kde byl očekáván objekt (uživatelem definovaný typ). Odkaz není objekt, ale vložený kód assembleru není schopný rozlišovat. Kompilátor generuje kód, jako by byl *objekt* instance.

## <a name="example"></a>Příklad

Následující ukázka generuje C4537 a ukazuje, jak ji opravit:

```cpp
// C4537.cpp
// compile with: /W1 /c
// processor: x86
struct S {
    int member;
};

void f1(S &s) {
    __asm mov eax, s.member;   // C4537
    // try the following code instead
    // or, make the declaration "void f1(S s)"
    /*
    mov eax, s
    mov eax, [eax]s.member
    */
}
```

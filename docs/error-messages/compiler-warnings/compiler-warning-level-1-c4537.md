---
title: Kompilátor upozornění (úroveň 1) C4537
ms.date: 08/27/2018
f1_keywords:
- C4537
helpviewer_keywords:
- C4537
ms.assetid: 9454493c-d419-475e-8f35-9c00233c9329
ms.openlocfilehash: 2f97be4e1aaa5143df685cb95935d350e6f02534
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441314"
---
# <a name="compiler-warning-level-1-c4537"></a>Kompilátor upozornění (úroveň 1) C4537

> "*objekt*": "*operátor*" použitý pro typ není UDT

## <a name="remarks"></a>Poznámky

Odkaz byl předán, kde byl očekáván objekt (uživatelem definovaný typ). Odkaz není objekt, ale není schopen provést rozdíl vloženého kódu assembleru. Kompilátor generuje kód, jako by *objektu* byly instance.

## <a name="example"></a>Příklad

Následující ukázka generuje C4537 a ukazuje, jak ho opravit:

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
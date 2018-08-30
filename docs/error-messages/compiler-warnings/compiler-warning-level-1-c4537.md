---
title: Upozornění (úroveň 1) C4537 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4537
dev_langs:
- C++
helpviewer_keywords:
- C4537
ms.assetid: 9454493c-d419-475e-8f35-9c00233c9329
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 052d11d5bdf269d950abe1ef761adc055cbc6ce3
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43213360"
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
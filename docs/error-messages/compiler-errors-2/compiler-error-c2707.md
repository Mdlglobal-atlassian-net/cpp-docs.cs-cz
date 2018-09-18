---
title: Chyba kompilátoru C2707 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2707
dev_langs:
- C++
helpviewer_keywords:
- C2707
ms.assetid: 3deaf45c-74da-4c9d-acc6-b82412720b74
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a8a9709b4bd6c66ec303ad61e2000ddc97976e87
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46107257"
---
# <a name="compiler-error-c2707"></a>Chyba kompilátoru C2707

'identifier': špatný kontext pro vnitřní funkci.

Vnitřní funkce strukturovaného zpracování výjimek nejsou platné v některých kontextech:

- `_exception_code()` mimo filtr výjimek nebo `__except` bloku

- `_exception_info()` mimo filtr výjimek

- `_abnormal_termination()` mimo `__finally` bloku

Chcete-li vyřešit chybu, ujistěte se, že zpracování výjimek vnitřní objekty jsou umístěny ve vhodném kontextu.

## <a name="example"></a>Příklad

Následující ukázka generuje C2707.

```
// C2707.cpp
#include <windows.h>
#include <stdio.h>

LONG MyFilter(LONG excode)
{
    return (excode == EXCEPTION_ACCESS_VIOLATION ?
        EXCEPTION_EXECUTE_HANDLER : EXCEPTION_CONTINUE_SEARCH);   // OK
}

LONG func(void)
{
    int x, y;
    return(GetExceptionCode() == EXCEPTION_ACCESS_VIOLATION ?  // C2707
             EXCEPTION_EXECUTE_HANDLER : EXCEPTION_CONTINUE_SEARCH);

    __try
    {
        y = 0;
        x = 4 / y;
        return 0;
     }

    __except(MyFilter(GetExceptionCode()))
    {
        return(GetExceptionCode() == EXCEPTION_ACCESS_VIOLATION ? // ok
               EXCEPTION_EXECUTE_HANDLER : EXCEPTION_CONTINUE_SEARCH);
    }
}

int main()
{
    __try
    {
        func();
    } __except(EXCEPTION_EXECUTE_HANDLER)
    {
        printf_s("Caught exception\n");
    }
}
```
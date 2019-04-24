---
title: Compiler Error C2707
ms.date: 11/04/2016
f1_keywords:
- C2707
helpviewer_keywords:
- C2707
ms.assetid: 3deaf45c-74da-4c9d-acc6-b82412720b74
ms.openlocfilehash: ce86f69b36b915b3e757b5d18430c99cb288e4e7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161001"
---
# <a name="compiler-error-c2707"></a>Compiler Error C2707

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
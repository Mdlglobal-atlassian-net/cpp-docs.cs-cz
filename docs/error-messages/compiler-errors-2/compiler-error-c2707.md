---
title: C2707 Chyba kompilátoru | Microsoft Docs
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
ms.openlocfilehash: bdbd957bb1c19e28d08dd0fa5392eadd0f019756
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33234053"
---
# <a name="compiler-error-c2707"></a>C2707 chyby kompilátoru
"identifikátor": Chybný kontext pro vnitřní funkce  
  
 Strukturované zpracování výjimek – vnitřní funkce jsou neplatné v některých kontextech:  
  
-   `_exception_code()` mimo filtru výjimek nebo `__except` bloku  
  
-   `_exception_info()` mimo filtru výjimek  
  
-   `_abnormal_termination()` mimo `__finally` bloku  
  
 Chcete-li vyřešit chyby, ujistěte se, že zpracování výjimek – vnitřní funkce jsou umístěny v odpovídající kontext.  
  
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
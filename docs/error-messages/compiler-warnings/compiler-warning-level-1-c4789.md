---
title: Kompilátoru (úroveň 1) upozornění C4789 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4789
dev_langs:
- C++
helpviewer_keywords:
- C4789
ms.assetid: 5800c301-5afb-4af0-85c1-ceb54d775234
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f8b16fada030783f5f9e3aa3d1f9a04e7743a13c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4789"></a>C4789 kompilátoru upozornění (úroveň 1)
bude přetečení vyrovnávací paměti identifikátor N velikost v bajtech; M bajtů se zapíšou začínající na posunu L  
  
 Upozorňuje přetečení v případě konkrétní C Runtime (CRT) funkce používají, vyrovnávací paměti parametry se jí předávají a přiřazení se provádí, tak, aby velikosti dat se ví, že v době kompilace. Toto upozornění je pro situace, které může elude typické neshoda velikost dat zjišťování.  
  
 Toto upozornění se zobrazí v případě dat, jehož délka je známá v doba kompilace, je zkopírovat a umístí do bloku dat, jejichž velikost se ví v době kompilace příliš malá pro data. Kopie je třeba provést pomocí jednoho z následujících funkcí CRT vnitřní formuláře:  
  
-   [strcpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)  
  
-   [memset](../../c-runtime-library/reference/memset-wmemset.md)  
  
-   [memcpy –](../../c-runtime-library/reference/memcpy-wmemcpy.md), [wmemcpy –](../../c-runtime-library/reference/memcpy-wmemcpy.md)  
  
 Toto upozornění se zobrazí také v případě datový typ parametru se neshoduje s použitím přetypování a pak dojde k pokusu o přiřazení kopírování z odkazu lvalue.  
  
 Visual C++, může vygenerovat upozornění pro kód cestu, která se někdy nepracuje. Toto upozornění můžete dočasně zakázat pomocí `#pragma`, jak je uvedeno v následujícím příkladu:  
  
 `#pragma(push)`  
  
 `#pragma warning ( disable : 4789 )`  
  
 `// unused code that generates compiler warning C4789`  
  
 `#pragma(pop)`  
  
 Díky tomu Visual C++ z generování upozornění pro tuto konkrétní blok kódu. `#pragma(push)` Zachová stávající stav před `#pragma warning(disable: 4789)` změní ho. `#pragma(pop)` Obnoví stisknutí stavu a odebere důsledky `#pragma warning(disable:4789)`. Další informace o direktivy preprocesoru C++ `#pragma`, najdete v části [upozornění](../../preprocessor/warning.md) a [direktivy Pragma a klíčové slovo __Pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4789.  
  
```  
// C4789.cpp  
// compile with: /Oi /W1 /c  
#include <string.h>  
#include <stdio.h>  
  
int main()   
{  
    char a[20];  
    strcpy(a, "0000000000000000000000000\n");   // C4789  
  
    char buf2[20];  
    memset(buf2, 'a', 21);   // C4789  
  
    char c;  
    wchar_t w = 0;  
    memcpy(&c, &w, sizeof(wchar_t));  
}  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří také C4789.  
  
```  
// C4789b.cpp  
// compile with: /W1 /O2 /c  
// processor: x86  
short G;  
  
void main()  
{  
   int * p = (int *)&G;   
   *p = 3;   // C4789 - writes an int through a pointer to short  
}   
```
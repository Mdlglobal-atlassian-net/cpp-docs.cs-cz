---
title: C2001 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2001
dev_langs:
- C++
helpviewer_keywords:
- C2001
ms.assetid: 0c3a7821-d8e5-4398-ab5a-4116d46e8dda
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f56eabbcb5ca322d7549c21a56893a8e13d9261
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2001"></a>C2001 chyby kompilátoru
nový řádek v konstantě  
  
 Řetězcová konstanta nemůže pokračovat na druhém řádku, pokud byste udělat následující:  
  
-   Ukončení první řádek s lomítkem.  
  
-   Řetězec na první řádek s uvozovky zavřete a otevřete řetězec na dalším řádku s jinou uvozovky.  
  
 Koncová první řádek s \n není dostatečná.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2001:  
  
```  
// C2001.cpp  
// C2001 expected  
#include <stdio.h>  
  
int main()  
{  
    printf_s("Hello,  
             world");  
    printf_s("Hello,\n  
             world");  
}  
```  
  
## <a name="example"></a>Příklad  
 Mezery na začátku na další řádek po znak pokračování řádku jsou součástí řetězcová konstanta. Žádná z výše uvedené příklady Nevkládejte znak nového řádku do řetězcová konstanta. Můžete vložit znak nového řádku, jak je vidět tady:  
  
```  
// C2001b.cpp  
#include <stdio.h>  
  
int main()  
{  
    printf_s("Hello,\n\  
             world");  
  
    printf_s("Hello,\  
             \nworld");  
  
    printf_s("Hello,\n"  
             "world");  
  
    printf_s("Hello,"  
             "\nworld");  
  
    printf_s("Hello,"  
             " world");  
  
    printf_s("Hello,\  
             world");  
}  
```
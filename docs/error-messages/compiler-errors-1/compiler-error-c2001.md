---
title: "C2001 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2001
dev_langs: C++
helpviewer_keywords: C2001
ms.assetid: 0c3a7821-d8e5-4398-ab5a-4116d46e8dda
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: aedba438451089aa2d71e06da7ce189ab97d4190
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
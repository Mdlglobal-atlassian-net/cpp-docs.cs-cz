---
title: "Kompilátoru (úroveň 1) upozornění C4744 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4744
dev_langs: C++
helpviewer_keywords: C4744
ms.assetid: f2a7d0b5-afd5-4926-abc3-cfbd367e3ff5
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0b6fa95f8477f889aa8664d2b6d99c753cb9848d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4744"></a>C4744 kompilátoru upozornění (úroveň 1)
'příkaz var' má jiný typ v 'file1' a 'file2': 'type1' a 'type2'.  
  
 Proměnná externí odkazuje nebo definované v dva soubory má různé typy v těchto souborů.  Vyřešit, zkontrolujte definic typů stejné nebo změnit název proměnné v jeden ze souborů.  
  
 C4744 jsou vydávány pouze v případě, že jsou soubory kompilovat s /GL.  Další informace najdete v tématu [/GL (optimalizace celého programu)](../../build/reference/gl-whole-program-optimization.md).  
  
> [!NOTE]
>  C4744 se obvykle dochází v souborech jazyka C (C++ není), protože v jazyce C++ je název proměnné upraven pomocí informací o typu.  Když (dole) ukázka zkompiluje jako C++, získáte chyba linkerů LNK2019.  
  
## <a name="example"></a>Příklad  
 Tato ukázka obsahuje první definice.  
  
```  
// C4744.c  
// compile with: /c /GL  
int global;  
```  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4744.  
  
```  
// C4744b.c  
// compile with: C4744.c /GL /W1  
// C4744 expected  
#include <stdio.h>  
  
extern unsigned global;  
  
main()   
{  
    printf_s("%d\n", global);  
}  
```
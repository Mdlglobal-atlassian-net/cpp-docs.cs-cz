---
title: "Kompilátoru (úroveň 1) upozornění C4674 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4674
dev_langs: C++
helpviewer_keywords: C4674
ms.assetid: 638dae0b-b82c-4865-9599-72630827ca09
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 43d34279ded00851962008837d0bf6cd76eaff7c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4674"></a>C4674 kompilátoru upozornění (úroveň 1)
"metody" musí být deklarován "statická" a mít přesně jeden parametr  
  
Podpis operátora převodu nebyl zadán správně. Metoda není považováno za převod definovaný uživatelem. Další informace o definování operátory najdete v tématu [uživatelem definované operátory (C + +/ CLI)](../../dotnet/user-defined-operators-cpp-cli.md) a [uživatelem definovaných převodů (C + +/ CLI)](../../dotnet/user-defined-conversions-cpp-cli.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4674.  
  
```  
// C4674.cpp  
// compile with: /clr /WX /W1 /LD  
ref class G {  
   int op_Implicit(int i) {   // C4674  
      return 0;  
   }  
};  
```  

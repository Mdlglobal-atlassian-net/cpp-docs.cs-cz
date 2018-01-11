---
title: "Kompilátoru (úroveň 4) upozornění C4460 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4460
dev_langs: C++
helpviewer_keywords: C4460
ms.assetid: c97ac1c9-598d-479e-bfff-c993690c4f3d
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: aa925e8d0ef7779f21485cb154b9b9209ce2388e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4460"></a>C4460 kompilátoru upozornění (úroveň 4)
WinRT nebo CLR operátor "operátor", byl předán parametr odkazem. WinRT nebo CLR operátor "operátor" má jinou sémantiku z C++ operátor 'operátor', máte v úmyslu předat hodnotu?  
  
 Předaný hodnotu odkazem uživatelské prostředí Windows Runtime nebo CLR operátor. Pokud je hodnota změněna uvnitř funkce, Všimněte si, že hodnota vrácena po volání funkce přiřadí návratovou hodnotu funkce. V jazyce C++ standardní změněné hodnoty se projeví po volání funkce.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4460 a ukazuje, jak ji odstranit.  
  
```  
// C4460.cpp  
// compile with: /W4 /clr   
#include <stdio.h>  
  
public value struct V {  
   static V operator ++(V& me) {   // C4460  
   // try the following line instead  
   // static V operator ++(V me) {  
  
      printf_s(__FUNCSIG__ " called\n");  
      V tmp = me;  
      me.m_i++;  
      return tmp;  
   }  
   int m_i;  
};  
  
int main() {  
   V v;  
   v.m_i = 0;  
  
   printf_s("%d\n", v.m_i);   // Should print 0  
   v++;   // Translates to "v = V::operator ++(v)"  
   printf_s("%d\n", v.m_i);   // will print 0, hence the warning  
}  
```
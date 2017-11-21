---
title: "Postupy: určení výstupního parametru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- function parameters
- out parameters
ms.assetid: 02862448-603c-4e9d-a5c5-b45fe38446e3
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c755be8e9a2358935bcfe9892f308cd2faedacd3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-specify-an-out-parameter"></a>Postupy: Určení výstupního parametru
Tento příklad ukazuje, jak určit, že parametr funkce je výstupní parametr a jak pro volání této funkce z programu v C#.  
  
 Výstupní parametr je zadán v jazyce Visual C++ s <xref:System.Runtime.InteropServices.OutAttribute> .  
  
## <a name="example"></a>Příklad  
 První část Tato ukázka je Visual C++ knihovna s typem, který obsahuje funkci s parametr typu out.  
  
```  
// cpp_out_param.cpp  
// compile with: /LD /clr:safe  
using namespace System;  
public value struct TestStruct {  
   static void Test([Runtime::InteropServices::Out] String^ %s) {  
      s = "a string";  
   }  
};  
```  
  
## <a name="example"></a>Příklad  
 Toto je klienta C#, který zpracovává komponentu Visual C++ vytvořili v předchozím příkladu.  
  
```  
// cpp_out_param_2.cs  
// compile with: /reference:cpp_out_param.dll  
using System;  
class TestClass {  
   public static void Main() {  
      String t;  
      TestStruct.Test(out t);  
      System.Console.WriteLine(t);  
   }  
}  
```  
  
```Output  
a string  
```  
  
## <a name="see-also"></a>Viz také  
 [Pomocí zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
---
title: 'Postupy: určení výstupního parametru | Microsoft Docs'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- function parameters
- out parameters
ms.assetid: 02862448-603c-4e9d-a5c5-b45fe38446e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: adc56a65829064376d2472206f916d32d369cb01
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
 [Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
---
title: "C2346 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2346
dev_langs: C++
helpviewer_keywords: C2346
ms.assetid: 246145be-5645-4cd6-867c-e3bc39e33dca
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 769d5addc47ead8ffb338d5fbef313cd46735d31
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2346"></a>C2346 chyby kompilátoru
'function' nelze kompilovat, jako nativní: důvod  
  
 Kompilátor nemohl zkompilovat funkce, která se MSIL.  
  
 Další informace najdete v tématu [spravované, nespravované](../../preprocessor/managed-unmanaged.md) a [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Funkce, která nemůže být zkompilovány do MSIL odebere kód.  
  
2.  Buď nelze kompilovat modul s **/CLR**, nebo označit jako nespravované s unmanaged – Direktiva pragma funkce.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2346.  
  
```  
// C2346.cpp  
// processor: x86  
// compile with: /clr   
// C2346 expected  
struct S  
{  
   S()  
   {  
      { __asm { nop } }  
   }  
   virtual __clrcall ~S() { }  
};  
  
void main()  
{  
   S s;  
}  
```
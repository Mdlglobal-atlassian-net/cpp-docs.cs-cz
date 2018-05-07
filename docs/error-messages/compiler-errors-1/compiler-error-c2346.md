---
title: C2346 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2346
dev_langs:
- C++
helpviewer_keywords:
- C2346
ms.assetid: 246145be-5645-4cd6-867c-e3bc39e33dca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9459d7330738180e92776e93fcba9a07bfd39640
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
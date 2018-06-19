---
title: Kompilátoru (úroveň 4) upozornění C4481 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4481
dev_langs:
- C++
helpviewer_keywords:
- C4481
ms.assetid: 7bfd4e0c-b452-4e6c-b7c4-ac5cc93fe4ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aeef5f2121808c5444af942fac0e3b72919f2354
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293115"
---
# <a name="compiler-warning-level-4-c4481"></a>C4481 kompilátoru upozornění (úroveň 4)
nestandardní rozšíření používané: override – specifikátor '– klíčové slovo'  
  
 Byl použit klíčové slovo, které nejsou v standard C++, například jeden specifikátorů override, které funguje taky v/CLR.  Další informace najdete v tématu,  
  
-   [/clr (kompilace modulu Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [Override – specifikátory](../../windows/override-specifiers-cpp-component-extensions.md)  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4481.  
  
```  
// C4481.cpp  
// compile with: /W4 /c  
class B {  
   virtual void f(unsigned);  
};  
  
class C : B {  
   void f(unsigned) override;   // C4481  
   void f2(unsigned);  
};  
```
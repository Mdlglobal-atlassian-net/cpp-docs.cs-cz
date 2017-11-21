---
title: "C3821 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3821
dev_langs: C++
helpviewer_keywords: C3821
ms.assetid: 2b327c7a-5faf-443c-ae82-944fae25b4df
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 47e0a2ed3c824ed1598f7e998d4966b95cc9233b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3821"></a>C3821 chyby kompilátoru
'function': spravovaný typ nebo funkci nelze použít v nespravované funkce  
  
 Funkcí s vloženým sestavením nebo [setjmp](../../c-runtime-library/reference/setjmp.md) nemůže obsahovat typy hodnot nebo spravované třídy. Chcete-li tuto chybu opravit, odeberte vloženého sestavení a `setjmp` nebo odebrání spravovaných objektů.  
  
 C3821 může také nastat, pokud se pokusíte použít automatické úložiště ve funkci vararg.  Další informace najdete v tématu [proměnné seznamy argumentů (...) (C + +/ CLI) ](../../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md) a [C++ – sémantika zásobníku pro odkazové typy](../../dotnet/cpp-stack-semantics-for-reference-types.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3821.  
  
```  
// C3821a.cpp  
// compile with: /clr /c  
public ref struct R {};  
void test1(...) {  
   R r;   // C3821  
}  
```  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3821.  
  
```  
// C3821b.cpp  
// compile with: /clr  
// processor: /x86  
ref class A {  
   public:  
   int i;  
};  
  
int main() {  
   // cannot use managed classes in this function  
   A ^a;     
  
   __asm {  
      nop  
   }  
} // C3821  
```  

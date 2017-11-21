---
title: Stack::POP (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::stack::pop
dev_langs: C++
helpviewer_keywords: pop member [STL/CLR]
ms.assetid: b7565385-9e6b-432d-8c71-c62c9c6ad90d
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1e461a312c75cdb6c9d33a1bfd59925372f60d5f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="stackpop-stlclr"></a>stack::pop (STL/CLR)
Odebere poslední element.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void pop();  
```  
  
## <a name="remarks"></a>Poznámky  
 Členská funkce odebere poslední elementu řízené sekvenci, která musí být neprázdný. Použijete jej tak, aby zkrátil zásobníku podle jednoho prvku na pozadí.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_stack_pop.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// pop an element and redisplay   
    c1.pop();   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / stack >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [Zásobník (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [Stack::push (STL/CLR)](../dotnet/stack-push-stl-clr.md)
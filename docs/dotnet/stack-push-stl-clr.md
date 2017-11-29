---
title: Stack::push (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::stack::push
dev_langs: C++
helpviewer_keywords: push member [STL/CLR]
ms.assetid: 60e5b076-c80f-4af0-a018-62cda7e081db
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 59f9122c7d341e3ad6064a2d97b90c4a2ceb22aa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="stackpush-stlclr"></a>stack::push (STL/CLR)
Přidá nový posledním elementem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void push(value_type val);  
```  
  
## <a name="remarks"></a>Poznámky  
 Členská funkce vloží element s hodnotou `val` na konci řízené sekvenci. Použít pro připojení jiný element se zásobníkem.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_stack_push.cpp   
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
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / stack >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [Zásobník (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [Stack::POP (STL/CLR)](../dotnet/stack-pop-stl-clr.md)
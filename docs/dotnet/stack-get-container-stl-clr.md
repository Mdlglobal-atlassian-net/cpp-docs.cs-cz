---
title: Stack::get_container (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::stack::get_container
dev_langs: C++
helpviewer_keywords: get_container member [STL/CLR]
ms.assetid: ba6fc541-fc18-4d1c-8e3f-6baaed427cbb
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5f6b0d984559c82fb283bfb563c3309936ede9b8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="stackgetcontainer-stlclr"></a>stack::get_container (STL/CLR)
Přístup k podkladové kontejneru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
container_type^ get_container();  
```  
  
## <a name="remarks"></a>Poznámky  
 Členská funkce vrátí popisovač pro základní kontejner. Můžete použít k porušení omezení způsobené obálku kontejneru.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_stack_get_container.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c" using container_type   
    Mystack::container_type wc1 = c1.get_container();   
    for each (wchar_t elem in wc1)   
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
 [Stack::container_type (STL/CLR)](../dotnet/stack-container-type-stl-clr.md)
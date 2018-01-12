---
title: Queue::POP (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::queue::pop
dev_langs: C++
helpviewer_keywords: pop member [STL/CLR]
ms.assetid: 38f6c03b-e8f8-4663-b3d6-18314cdc8e7d
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8521ea0a85b8a4997f38a6236981d85b82ecc884
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="queuepop-stlclr"></a>queue::pop (STL/CLR)
Odebere poslední element.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void pop();  
```  
  
## <a name="remarks"></a>Poznámky  
 Členská funkce odebere poslední elementu řízené sekvenci, která musí být neprázdný. Použijete jej tak, aby zkrátil fronty podle jednoho prvku na pozadí.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_queue_pop.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
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
b c  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / fronty >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [fronty (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [queue::push (STL/CLR)](../dotnet/queue-push-stl-clr.md)
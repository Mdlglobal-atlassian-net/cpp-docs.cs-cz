---
title: priority_queue::value_type (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::priority_queue::value_type
dev_langs: C++
helpviewer_keywords: value_type member [STL/CLR]
ms.assetid: 0d81ef75-8bd1-44f5-8753-4b42a505d8c3
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b9c1b2966e1ff023fe61fa64e49872a443f00c19
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="priorityqueuevaluetype-stlclr"></a>priority_queue::value_type (STL/CLR)
Typ prvku  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef Value value_type;  
```  
  
## <a name="remarks"></a>Poznámky  
 Typ je synonymum pro parametr šablony `Value`.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_priority_queue_value_type.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display reversed contents " a b c" using value_type   
    for (; !c1.empty(); c1.pop())   
        {   // store element in value_type object   
        Mypriority_queue::value_type val = c1.top();   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c b a  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / fronty >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [priority_queue::const_reference (STL/CLR)](../dotnet/priority-queue-const-reference-stl-clr.md)   
 [priority_queue::Reference (STL/CLR)](../dotnet/priority-queue-reference-stl-clr.md)
---
title: priority_queue::size (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::priority_queue::size
dev_langs: C++
helpviewer_keywords: size member [STL/CLR]
ms.assetid: 37ef4be3-daac-4b5a-9a00-085863f694e0
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7cb89416afceca65e42ad3a54b7903554af2e0d9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="priorityqueuesize-stlclr"></a>priority_queue::size (STL/CLR)
Spočítá počet prvků.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
size_type size();  
```  
  
## <a name="remarks"></a>Poznámky  
 Členská funkce vrátí délku řízené sekvenci. Použijte k určení počtu elementy aktuálně v řízené sekvenci. Pokud všechny se zajímáte o tom, jestli má pořadí nenulové hodnoty velikosti, najdete v části [priority_queue::empty (STL/CLR)](../dotnet/priority-queue-empty-stl-clr.md)`()`.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_priority_queue_size.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());   
  
// pop an item and reinspect   
    c1.pop();   
    System::Console::WriteLine("size() = {0} after popping", c1.size());   
  
// add two elements and reinspect   
    c1.push(L'a');   
    c1.push(L'b');   
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 c a b  
size() = 3 starting with 3  
size() = 2 after popping  
size() = 4 after adding 2  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / fronty >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [priority_queue::Empty (STL/CLR)](../dotnet/priority-queue-empty-stl-clr.md)
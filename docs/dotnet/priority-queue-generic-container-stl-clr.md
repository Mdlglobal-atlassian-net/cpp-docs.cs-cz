---
title: priority_queue::generic_container (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::priority_queue::generic_container
dev_langs: C++
helpviewer_keywords: generic_container member [STL/CLR]
ms.assetid: b938c433-7ef1-4077-93c2-2aee8ddf4d67
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: db6717b124eb04a98060da7b02d391e7d067d0ee
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="priorityqueuegenericcontainer-stlclr"></a>priority_queue::generic_container (STL/CLR)
Typ generické rozhraní pro kontejner.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef Microsoft::VisualC::StlClr::IPriorityQueue<Value>  
    generic_container;  
```  
  
## <a name="remarks"></a>Poznámky  
 Typ popisuje obecné rozhraní pro tuto třídu kontejneru adaptér šablony.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_priority_queue_generic_container.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Mypriority_queue::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1->get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    gc1->push(L'd');   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify original and display generic   
    c1.push(L'e');   
    for each (wchar_t elem in gc1->get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c a b  
c a b  
d c b a  
e d b a c  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / fronty >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)
---
title: Queue::back_item (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::queue::back_item
dev_langs: C++
helpviewer_keywords: back_item member [STL/CLR]
ms.assetid: 721e44e1-eb46-41bf-8b3c-0fcbc02fb155
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d11e25d4ca4e865a75043927461567cfb2092838
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="queuebackitem-stlclr"></a>queue::back_item (STL/CLR)
Přístup k posledním elementem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
property value_type back_item;  
```  
  
## <a name="remarks"></a>Poznámky  
 Vlastnost přistupuje ke poslední elementu řízené sekvenci, která musí být neprázdný. Použijete jej číst nebo zapisovat posledním elementem, když víte, že existuje.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_queue_back_item.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("back_item = {0}", c1.back_item);   
  
// alter last item and reinspect   
    c1.back_item = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
back_item = c  
 a b x  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / fronty >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [fronty (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [Queue::back (STL/CLR)](../dotnet/queue-back-stl-clr.md)   
 [Queue::front (STL/CLR)](../dotnet/queue-front-stl-clr.md)   
 [Queue::front_item (STL/CLR)](../dotnet/queue-front-item-stl-clr.md)
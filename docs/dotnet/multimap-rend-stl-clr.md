---
title: multimap::rend (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::multimap::rend
dev_langs: C++
helpviewer_keywords: rend member [STL/CLR]
ms.assetid: f8d3f683-eeab-4a8b-af3f-fb6653114594
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 72ca29c14f4395f6505386efdda7f27e637219eb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="multimaprend-stlclr"></a>multimap::rend (STL/CLR)
Označuje konec odstínech řízené sekvenci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
reverse_iterator rend();  
```  
  
## <a name="remarks"></a>Poznámky  
 Členská funkce vrátí zpětné iterator této body právě nad rámec začátku řízené sekvenci. Proto označí `end` zpětné pořadí. Můžete ji použít k získání iterátor, který označuje `current` konec řízené sekvenci vidět v obráceném pořadí, ale jeho stav můžete změnit, pokud se změní délka řízené sekvenci.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_multimap_rend.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::multimap<wchar_t, int> Mymultimap;   
int main()   
    {   
    Mymultimap c1;   
    c1.insert(Mymultimap::make_value(L'a', 1));   
    c1.insert(Mymultimap::make_value(L'b', 2));   
    c1.insert(Mymultimap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymultimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// inspect first two items in reversed sequence   
    Mymultimap::reverse_iterator rit = c1.rend();   
    --rit;   
    --rit;   
    System::Console::WriteLine("*-- --rend() = [{0} {1}]",   
        rit->first, rit->second);   
    ++rit;   
    System::Console::WriteLine("*--rend() = [{0} {1}]",   
        rit->first, rit->second);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
*-- --rend() = [b 2]  
*--rend() = [a 1]  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / map >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [multimap (STL/CLR)](../dotnet/multimap-stl-clr.md)   
 [multimap::begin (STL/CLR)](../dotnet/multimap-begin-stl-clr.md)   
 [multimap::end (STL/CLR)](../dotnet/multimap-end-stl-clr.md)   
 [multimap::rbegin (STL/CLR)](../dotnet/multimap-rbegin-stl-clr.md)
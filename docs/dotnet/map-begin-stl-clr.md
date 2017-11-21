---
title: map::begin (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::map::begin
dev_langs: C++
helpviewer_keywords: begin member [STL/CLR]
ms.assetid: a909d278-6214-4e11-984d-509fa528bfa3
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 45dc4d34fe184bbdf1f9b250df3983a70e413d97
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="mapbegin-stlclr"></a>map::begin (STL/CLR)
Určuje začátek řízené sekvence.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
iterator begin();  
```  
  
## <a name="remarks"></a>Poznámky  
 Členská funkce vrátí obousměrného iterator, který určuje první elementu v řízené sekvenci nebo právě přesahuje za konec prázdnou sekvencí. Můžete ji použít k získání iterátor, který označuje `current` začátku řízené sekvenci, ale jeho stav můžete změnit, pokud se změní délka řízené sekvenci.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_map_begin.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// inspect first two items   
    Mymap::iterator it = c1.begin();   
    System::Console::WriteLine("*begin() = [{0} {1}]",   
        it->first, it->second);   
    ++it;   
    System::Console::WriteLine("*++begin() = [{0} {1}]",   
        it->first, it->second);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
*begin() = [a 1]  
*++begin() = [b 2]  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / map >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [mapy (STL/CLR)](../dotnet/map-stl-clr.md)   
 [map::end (STL/CLR)](../dotnet/map-end-stl-clr.md)
---
title: map::mapped_type (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::map::mapped_type
dev_langs: C++
helpviewer_keywords: mapped_type member [STL/CLR]
ms.assetid: 818ee40d-8355-446e-a7b2-eb5bf8cc689d
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ac5a39ed59b224304b0c8f2095a032bf39daef48
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="mapmappedtype-stlclr"></a>map::mapped_type (STL/CLR)
Typ mapované hodnoty přiřazené ke každému klíči  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef Mapped mapped_type;  
```  
  
## <a name="remarks"></a>Poznámky  
 Typ je synonymum pro parametr šablony `Mapped`.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_map_mapped_type.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]" using mapped_type   
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in mapped_type object   
        Mymap::mapped_type val = it->second;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
1 2 3  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / map >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [mapy (STL/CLR)](../dotnet/map-stl-clr.md)   
 [map::key_compare (STL/CLR)](../dotnet/map-key-compare-stl-clr.md)   
 [map::value_type (STL/CLR)](../dotnet/map-value-type-stl-clr.md)
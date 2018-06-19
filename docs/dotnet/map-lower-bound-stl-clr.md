---
title: map::lower_bound (STL/CLR) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::map::lower_bound
dev_langs:
- C++
helpviewer_keywords:
- lower_bound member [STL/CLR]
ms.assetid: 959651a0-f949-4cc1-859b-248b6930f16c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 679288e021d651d51d98fbe18701aed62f591275
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33137800"
---
# <a name="maplowerbound-stlclr"></a>map::lower_bound (STL/CLR)
Najde začátek rozsahu, který odpovídá zadaným klíčem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
iterator lower_bound(key_type key);  
```  
  
#### <a name="parameters"></a>Parametry  
 klíč  
 Hodnota klíče pro vyhledávání.  
  
## <a name="remarks"></a>Poznámky  
 Členská funkce určuje první prvek `X` v řízené sekvenci, který má ekvivalentní řazení do `key`. Pokud žádný takový prvek existuje, vrátí [map::end (STL/CLR)](../dotnet/map-end-stl-clr.md)`()`; jinak vrátí iterátor, který označuje `X`. Použijte jej k vyhledání na začátek pořadí prvků, které jsou aktuálně v řízené sekvenci, které odpovídají zadaným klíčem.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_map_lower_bound.cpp   
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
  
    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",   
        c1.lower_bound(L'x') == c1.end());   
  
    Mymap::iterator it = c1.lower_bound(L'a');   
    System::Console::WriteLine("*lower_bound(L'a') = [{0} {1}]",   
        it->first, it->second);   
    it = c1.lower_bound(L'b');   
    System::Console::WriteLine("*lower_bound(L'b') = [{0} {1}]",   
        it->first, it->second);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
lower_bound(L'x')==end() = True  
*lower_bound(L'a') = [a 1]  
*lower_bound(L'b') = [b 2]  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / map >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [mapy (STL/CLR)](../dotnet/map-stl-clr.md)   
 [map::Count (STL/CLR)](../dotnet/map-count-stl-clr.md)   
 [map::equal_range (STL/CLR)](../dotnet/map-equal-range-stl-clr.md)   
 [map::Find (STL/CLR)](../dotnet/map-find-stl-clr.md)   
 [map::upper_bound (STL/CLR)](../dotnet/map-upper-bound-stl-clr.md)
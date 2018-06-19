---
title: hash_map::size (STL/CLR) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_map::size
dev_langs:
- C++
helpviewer_keywords:
- size member [STL/CLR]
ms.assetid: 5eb91502-1b11-4703-b473-eb609c181b74
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c97d3f89bc26a7f50ab4dbbe175e3996cd7377f7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33109879"
---
# <a name="hashmapsize-stlclr"></a>hash_map::size (STL/CLR)
Spočítá počet prvků.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
size_type size();  
```  
  
## <a name="remarks"></a>Poznámky  
 Členská funkce vrátí délku řízené sekvenci. Použijte k určení počtu elementy aktuálně v řízené sekvenci. Pokud všechny se zajímáte o tom, jestli má pořadí nenulové hodnoty velikosti, najdete v části [hash_map::empty (STL/CLR)](../dotnet/hash-map-empty-stl-clr.md)`()`.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_hash_map_size.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0} after clearing", c1.size());   
  
// add elements and clear again   
    c1.insert(Myhash_map::make_value(L'd', 4));   
    c1.insert(Myhash_map::make_value(L'e', 5));   
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
size() = 0 after clearing  
size() = 2 after adding 2  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / hash_map >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [hash_map – (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_map::empty (STL/CLR)](../dotnet/hash-map-empty-stl-clr.md)
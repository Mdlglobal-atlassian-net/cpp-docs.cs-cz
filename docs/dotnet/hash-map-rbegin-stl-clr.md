---
title: hash_map::rbegin (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::hash_map::rbegin
dev_langs:
- C++
helpviewer_keywords:
- rbegin member [STL/CLR]
ms.assetid: e3b6c4d5-9482-471e-b5fc-70331b082a9b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4f3f87fd1ba0e2f09885a01e712a05ba99faf442
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="hashmaprbegin-stlclr"></a>hash_map::rbegin (STL/CLR)
Označuje začátek odstínech řízené sekvenci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
reverse_iterator rbegin();  
```  
  
## <a name="remarks"></a>Poznámky  
 Členská funkce vrátí zpětné iterator, který určuje poslední elementu v řízené sekvenci nebo právě nad rámec začátku prázdnou sekvencí. Proto označí `beginning` zpětné pořadí. Můžete ji použít k získání iterátor, který označuje `current` začátku řízené sekvenci vidět v obráceném pořadí, ale jeho stav můžete změnit, pokud se změní délka řízené sekvenci.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_hash_map_rbegin.cpp   
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
  
// inspect first two items in reversed sequence   
    Myhash_map::reverse_iterator rit = c1.rbegin();   
    System::Console::WriteLine("*rbegin() = [{0} {1}]",   
        rit->first, rit->second);   
    ++rit;   
    System::Console::WriteLine("*++rbegin() = [{0} {1}]",   
        rit->first, rit->second);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
*rbegin() = [c 3]  
*++rbegin() = [b 2]  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / hash_map >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [hash_map – (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_map::begin (STL/CLR)](../dotnet/hash-map-begin-stl-clr.md)   
 [hash_map::end (STL/CLR)](../dotnet/hash-map-end-stl-clr.md)   
 [hash_map::rend (STL/CLR)](../dotnet/hash-map-rend-stl-clr.md)
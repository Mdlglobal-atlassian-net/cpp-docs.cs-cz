---
title: hash_multimap::Count (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::hash_multimap::Count
dev_langs: C++
helpviewer_keywords: count member [STL/CLR]
ms.assetid: a4bc5b19-e025-4063-9797-304ab4ba08aa
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 53f8249f112064b49fc159439078f16d7e1f58ed
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="hashmultimapcount-stlclr"></a>hash_multimap::count (STL/CLR)
Zjistí počet prvků odpovídající zadanému klíči.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
size_type count(key_type key);  
```  
  
#### <a name="parameters"></a>Parametry  
 klíč  
 Hodnota klíče pro vyhledávání.  
  
## <a name="remarks"></a>Poznámky  
 Členská funkce vrátí počet prvků v řízené sekvenci, které mají ekvivalentní řazení s `key`. Použijte k určení počtu elementy aktuálně v řízené sekvenci, které odpovídají zadaným klíčem.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_hash_multimap_count.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_multimap<wchar_t, int> Myhash_multimap;   
int main()   
    {   
    Myhash_multimap c1;   
    c1.insert(Myhash_multimap::make_value(L'a', 1));   
    c1.insert(Myhash_multimap::make_value(L'b', 2));   
    c1.insert(Myhash_multimap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_multimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("count(L'A') = {0}", c1.count(L'A'));   
    System::Console::WriteLine("count(L'b') = {0}", c1.count(L'b'));   
    System::Console::WriteLine("count(L'C') = {0}", c1.count(L'C'));   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
count(L'A') = 0  
count(L'b') = 1  
count(L'C') = 0  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / hash_map >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [hash_multimap (STL/CLR)](../dotnet/hash-multimap-stl-clr.md)   
 [hash_multimap::equal_range (STL/CLR)](../dotnet/hash-multimap-equal-range-stl-clr.md)
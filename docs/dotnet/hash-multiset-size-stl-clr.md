---
title: hash_multiset::size (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::hash_multiset::size
dev_langs: C++
helpviewer_keywords: size member [STL/CLR]
ms.assetid: 45f1f35e-35c4-4e39-8485-0786c1de22e3
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fce1f75c546e245c3007fefe1c993d5f9260c43d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="hashmultisetsize-stlclr"></a>hash_multiset::size (STL/CLR)
Spočítá počet prvků.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
size_type size();  
```  
  
## <a name="remarks"></a>Poznámky  
 Členská funkce vrátí délku řízené sekvenci. Použijte k určení počtu elementy aktuálně v řízené sekvenci. Pokud všechny se zajímáte o tom, jestli má pořadí nenulové hodnoty velikosti, najdete v části [hash_multiset::empty (STL/CLR)](../dotnet/hash-multiset-empty-stl-clr.md)`()`.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_hash_multiset_size.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0} after clearing", c1.size());   
  
// add elements and clear again   
    c1.insert(L'a');   
    c1.insert(L'b');   
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
size() = 3 starting with 3  
size() = 0 after clearing  
size() = 2 after adding 2  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / hash_set >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_multiset::Empty (STL/CLR)](../dotnet/hash-multiset-empty-stl-clr.md)
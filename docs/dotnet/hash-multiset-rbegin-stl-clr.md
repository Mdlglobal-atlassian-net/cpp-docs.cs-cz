---
title: hash_multiset::rbegin (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::hash_multiset::rbegin
dev_langs: C++
helpviewer_keywords: rbegin member [STL/CLR]
ms.assetid: 69a06d99-3262-495b-9956-5f155162da33
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 898c7e25482f1a1984e7093ac5a77c0b98ec2799
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="hashmultisetrbegin-stlclr"></a>hash_multiset::rbegin (STL/CLR)
Označuje začátek odstínech řízené sekvenci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
reverse_iterator rbegin();  
```  
  
## <a name="remarks"></a>Poznámky  
 Členská funkce vrátí zpětné iterator, který určuje poslední elementu v řízené sekvenci nebo právě nad rámec začátku prázdnou sekvencí. Proto označí `beginning` zpětné pořadí. Můžete ji použít k získání iterátor, který označuje `current` začátku řízené sekvenci vidět v obráceném pořadí, ale jeho stav můžete změnit, pokud se změní délka řízené sekvenci.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_hash_multiset_rbegin.cpp   
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
  
// inspect first two items in reversed sequence   
    Myhash_multiset::reverse_iterator rit = c1.rbegin();   
    System::Console::WriteLine("*rbegin() = {0}", *rit);   
    System::Console::WriteLine("*++rbegin() = {0}", *++rit);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*rbegin() = c  
*++rbegin() = b  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / hash_set >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_multiset::begin (STL/CLR)](../dotnet/hash-multiset-begin-stl-clr.md)   
 [hash_multiset::end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md)   
 [hash_multiset::rend (STL/CLR)](../dotnet/hash-multiset-rend-stl-clr.md)
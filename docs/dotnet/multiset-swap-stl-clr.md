---
title: multiset::swap (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::multiset::swap
dev_langs: C++
helpviewer_keywords: swap member [STL/CLR]
ms.assetid: 8a3023c7-e58b-4ffe-8fd5-2e0bf02cc291
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b520cb617b4a8fed151d0c2f473cce75c7594178
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="multisetswap-stlclr"></a>multiset::swap (STL/CLR)
Zamění obsah dvou kontejnerů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void swap(multiset<Key>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 vpravo  
 Kontejner se Prohodit obsah s.  
  
## <a name="remarks"></a>Poznámky  
 Členská funkce prohození řízené pořadí mezi `this` a `right`. Dělá to tak včas konstantní a vyvolá žádné výjimky. Můžete ho použít jako rychlý způsob, jak exchange obsah dva kontejnery.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_multiset_swap.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct another container with repetition of values   
    Mymultiset c2;   
    c2.insert(L'd');   
    c2.insert(L'e');   
    c2.insert(L'f');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// swap and redisplay   
    c1.swap(c2);   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
d e f  
d e f  
a b c  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – nebo nastavení >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [multiset (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [multiset::Operator = (STL/CLR)](../dotnet/multiset-operator-assign-stl-clr.md)
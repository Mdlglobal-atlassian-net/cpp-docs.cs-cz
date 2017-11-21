---
title: multiset::generic_value (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::multiset::generic_value
dev_langs: C++
helpviewer_keywords: generic_value member [STL/CLR]
ms.assetid: 4b77b5f8-1e69-48b3-b523-c92ab538a29f
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0d24566b6a95be13da160dd03709291edd14ebcf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="multisetgenericvalue-stlclr"></a>multiset::generic_value (STL/CLR)
Typ elementu pro použití s generické rozhraní pro kontejner.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef GValue generic_value;  
```  
  
## <a name="remarks"></a>Poznámky  
 Popisuje typ objektu typu `GValue` , který popisuje element uložené hodnoty pro použití s obecné rozhraní pro tuto třídu kontejneru šablony.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_multiset_generic_value.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Mymultiset::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Mymultiset::generic_iterator gcit = gc1->begin();   
    Mymultiset::generic_value gcval = *gcit;   
    System::Console::WriteLine(" {0}", gcval);   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – nebo nastavení >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [multiset (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [multiset::generic_container (STL/CLR)](../dotnet/multiset-generic-container-stl-clr.md)   
 [multiset::generic_iterator (STL/CLR)](../dotnet/multiset-generic-iterator-stl-clr.md)   
 [multiset::generic_reverse_iterator (STL/CLR)](../dotnet/multiset-generic-reverse-iterator-stl-clr.md)
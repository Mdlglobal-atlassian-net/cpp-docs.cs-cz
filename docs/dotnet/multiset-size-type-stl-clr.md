---
title: multiset::size_type (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::multiset::size_type
dev_langs: C++
helpviewer_keywords: size_type member [STL/CLR]
ms.assetid: 6ddadf69-ab2d-4b06-a59c-982c2e29f718
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5958883ffc1d4c194061f01428ff3c7dd3a9866b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="multisetsizetype-stlclr"></a>multiset::size_type (STL/CLR)
Typ podepsaný vzdálenost mezi dvěma elementu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef int size_type;  
```  
  
## <a name="remarks"></a>Poznámky  
 Typ popisuje element záporný počet.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_multiset_size_type.cpp   
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
  
// compute positive difference   
    Mymultiset::size_type diff = 0;   
    for (Mymultiset::iterator it = c1.begin(); it != c1.end(); ++it)   
        ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
end()-begin() = 3  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – nebo nastavení >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [multiset (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [multiset::Empty (STL/CLR)](../dotnet/multiset-empty-stl-clr.md)
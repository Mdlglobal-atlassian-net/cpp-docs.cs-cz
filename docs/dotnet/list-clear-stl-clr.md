---
title: list::clear (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::list::clear
dev_langs: C++
helpviewer_keywords: clear member [STL/CLR]
ms.assetid: 5aac9a64-52f6-4a73-8b24-e30ceedcbc20
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 140ca420bd84dd20a1162c43e078b73c58f6a494
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="listclear-stlclr"></a>list::clear (STL/CLR)
Odebere všechny prvky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void clear();  
```  
  
## <a name="remarks"></a>Poznámky  
 Členská funkce efektivně volá [list::erase (STL/CLR)](../dotnet/list-erase-stl-clr.md) `(` [list::begin (STL/CLR)](../dotnet/list-begin-stl-clr.md) `(),` [list::end (STL/CLR)](../dotnet/list-end-stl-clr.md) `())`. Použijte k zajištění, že řízené sekvenci je prázdný.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_list_clear.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// add elements and clear again   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
  
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
size() = 0  
 a b  
size() = 0  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – nebo jejich výpisu >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [seznam (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list::Erase (STL/CLR)](../dotnet/list-erase-stl-clr.md)
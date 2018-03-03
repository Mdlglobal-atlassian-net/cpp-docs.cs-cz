---
title: deque::rbegin (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::deque::rbegin
dev_langs:
- C++
helpviewer_keywords:
- rbegin member [STL/CLR]
ms.assetid: 5d399c1d-bd7e-4b2e-bde0-11a000e29679
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d111fc2739dba0b6a8531c6fe5a8b149b901f818
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="dequerbegin-stlclr"></a>deque::rbegin (STL/CLR)
Označuje začátek odstínech řízené sekvenci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
reverse_iterator rbegin();  
```  
  
## <a name="remarks"></a>Poznámky  
 Členská funkce vrátí zpětné iterator, který určuje poslední elementu v řízené sekvenci nebo právě nad rámec začátku prázdnou sekvencí. Proto označí `beginning` zpětné pořadí. Můžete ji použít k získání iterátor, který označuje `current` začátku řízené sekvenci vidět v obráceném pořadí, ale jeho stav můžete změnit, pokud se změní délka řízené sekvenci.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_deque_rbegin.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items in reversed sequence   
    cliext::deque<wchar_t>::reverse_iterator rit = c1.rbegin();   
    System::Console::WriteLine("*rbegin() = {0}", *rit);   
    System::Console::WriteLine("*++rbegin() = {0}", *++rit);   
  
// alter first two items and reinspect   
    *--rit = L'x';   
    *++rit = L'y';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*rbegin() = c  
*++rbegin() = b  
 a y x  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / deque >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [deque::begin (STL/CLR)](../dotnet/deque-begin-stl-clr.md)   
 [deque::end (STL/CLR)](../dotnet/deque-end-stl-clr.md)   
 [deque::rend (STL/CLR)](../dotnet/deque-rend-stl-clr.md)
---
title: "operátor&lt; (list) (STL/CLR) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::list::operator<
dev_langs: C++
helpviewer_keywords: operator< member [STL/CLR]
ms.assetid: 6990fac2-3eeb-481f-b289-1c93f51422e4
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c7bb90de77600fcef5925268fb9d55785bcdef3c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="operatorlt-list-stlclr"></a>operátor&lt; (list) (STL/CLR)
Seznam menší než porovnání.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value>  
    bool operator<(list<Value>% left,  
        list<Value>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 left  
 Levé kontejner k porovnání.  
  
 vpravo  
 Správném kontejneru k porovnání.  
  
## <a name="remarks"></a>Poznámky  
 Operátor funkce vrátí hodnotu true, pokud, pro nejnižší pozici `i` pro kterou `!(right[i] < left[i])` je také hodnotu true, `left[i] < right[i]`. Funkce `left->size() < right->size()` použijete k testování zda `left` je seřadí před `right` při dva seznamy jsou porovná s prvkem elementu.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_list_operator_lt.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::list<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] < [a b c] is {0}",   
        c1 < c1);   
    System::Console::WriteLine("[a b c] < [a b d] is {0}",   
        c1 < c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] < [a b c] is False  
[a b c] < [a b d] is True  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – nebo jejich výpisu >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [seznam (STL/CLR)](../dotnet/list-stl-clr.md)   
 [Operator == (list) (STL/CLR)](../dotnet/operator-equality-list-stl-clr.md)   
 [Operator! = (list) (STL/CLR)](../dotnet/operator-inequality-list-stl-clr.md)   
 [Operator > = (list) (STL/CLR)](../dotnet/operator-greater-or-equal-list-stl-clr.md)   
 [Operator > (list) (STL/CLR)](../dotnet/operator-greater-than-list-stl-clr.md)   
 [Operator < = (list) (STL/CLR)](../dotnet/operator-less-or-equal-list-stl-clr.md)
---
title: "operátor&gt;= (set) (STL/CLR) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::set::operator>=
dev_langs: C++
helpviewer_keywords: operator>= member [STL/CLR]
ms.assetid: d08a0fc9-02e4-4e05-b469-bac325c38370
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 37b295712e1a6bd0703c4ca0ed09675622ad8b70
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="operatorgt-set-stlclr"></a>operátor&gt;= (set) (STL/CLR)
Seznam větší než nebo rovna porovnání.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Key>  
    bool operator>=(set<Key>% left,  
        set<Key>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 left  
 Levé kontejner k porovnání.  
  
 vpravo  
 Správném kontejneru k porovnání.  
  
## <a name="remarks"></a>Poznámky  
 Operátor funkce vrátí hodnotu `!(left < right)`. Můžete použít k testování zda `left` není seřadí před `right` při dvě sady jsou porovná s prvkem elementu.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_set_operator_ge.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myset c2;   
    c2.insert(L'a');   
    c2.insert(L'b');   
    c2.insert(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] >= [a b c] is {0}",   
        c1 >= c1);   
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",   
        c1 >= c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] >= [a b c] is True  
[a b c] >= [a b d] is False  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – nebo nastavení >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [Sada (STL/CLR)](../dotnet/set-stl-clr.md)   
 [Operator == (set) (STL/CLR)](../dotnet/operator-equality-set-stl-clr.md)   
 [Operator! = (set) (STL/CLR)](../dotnet/operator-inequality-set-stl-clr.md)   
 [operátor\< (set) (STL/CLR)](../dotnet/operator-less-than-set-stl-clr.md)   
 [Operator > (set) (STL/CLR)](../dotnet/operator-greater-than-set-stl-clr.md)   
 [Operator < = (set) (STL/CLR)](../dotnet/operator-less-or-equal-set-stl-clr.md)
---
title: "operátor&lt;= (multimap) (STL/CLR) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::multimap::operator<=
dev_langs: C++
helpviewer_keywords: operator<= member [STL/CLR]
ms.assetid: f23cdacd-fb1b-4e87-8e32-497226841871
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e628a37c2099dcc9287139b457fb98f2f9602b08
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="operatorlt-multimap-stlclr"></a>operátor&lt;= (multimap) (STL/CLR)
Seznam menší než nebo rovna porovnání.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Key,  
    typename Mapped>  
    bool operator<=(multimap<Key, Mapped>% left,  
        multimap<Key, Mapped>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 left  
 Levé kontejner k porovnání.  
  
 vpravo  
 Správném kontejneru k porovnání.  
  
## <a name="remarks"></a>Poznámky  
 Operátor funkce vrátí hodnotu `!(right < left)`. Můžete použít k testování zda `left` není objednaný po `right` po dvou multimaps jsou porovná s prvkem elementu.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_multimap_operator_le.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::multimap<wchar_t, int> Mymultimap;   
int main()   
    {   
    Mymultimap c1;   
    c1.insert(Mymultimap::make_value(L'a', 1));   
    c1.insert(Mymultimap::make_value(L'b', 2));   
    c1.insert(Mymultimap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymultimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymultimap c2;   
    c2.insert(Mymultimap::make_value(L'a', 1));   
    c2.insert(Mymultimap::make_value(L'b', 2));   
    c2.insert(Mymultimap::make_value(L'd', 4));   
  
// display contents " [a 1] [b 2] [d 4]"   
    for each (Mymultimap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] <= [a b c] is {0}",   
        c1 <= c1);   
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",   
        c2 <= c1);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
 [a 1] [b 2] [d 4]  
[a b c] <= [a b c] is True  
[a b d] <= [a b c] is False  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / map >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [multimap (STL/CLR)](../dotnet/multimap-stl-clr.md)   
 [Operator == (multimap) (STL/CLR)](../dotnet/operator-equality-multimap-stl-clr.md)   
 [Operator! = (multimap) (STL/CLR)](../dotnet/operator-inequality-multimap-stl-clr.md)   
 [operátor\< (multimap) (STL/CLR)](../dotnet/operator-less-than-multimap-stl-clr.md)   
 [Operator > = (multimap) (STL/CLR)](../dotnet/operator-greater-or-equal-multimap-stl-clr.md)   
 [Operator > (multimap) (STL/CLR)](../dotnet/operator-greater-than-multimap-stl-clr.md)
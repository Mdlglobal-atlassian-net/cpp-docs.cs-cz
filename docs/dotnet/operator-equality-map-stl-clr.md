---
title: Operator == (map) (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::map::operator==
dev_langs: C++
helpviewer_keywords: operator== member [STL/CLR]
ms.assetid: 6f7672af-71f8-4086-ac42-173203e52951
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6c4504056574ab16ecc26ba84499c4d92851d2ad
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="operator-map-stlclr"></a>operator== (map) – operátor (STL/CLR)
Zobrazí seznam rovna porovnání.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Key,  
    typename Mapped>  
    bool operator==(map<Key, Mapped>% left,  
        map<Key, Mapped>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 left  
 Levé kontejner k porovnání.  
  
 vpravo  
 Správném kontejneru k porovnání.  
  
## <a name="remarks"></a>Poznámky  
 Operátor funkce vrátí hodnotu true pouze v případě, že daná pořadí řízené `left` a `right` mít stejnou délku a pro každou pozici `i`, `left[i] ==` `right[i]`. Můžete použít k testování zda `left` je stejný jako seřazené `right` při dvě mapy jsou porovná s prvkem elementu.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_map_operator_eq.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymap c2;   
    c2.insert(Mymap::make_value(L'a', 1));   
    c2.insert(Mymap::make_value(L'b', 2));   
    c2.insert(Mymap::make_value(L'd', 4));   
  
// display contents " [a 1] [b 2] [d 4]"   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] == [a b c] is {0}",   
        c1 == c1);   
    System::Console::WriteLine("[a b c] == [a b d] is {0}",   
        c1 == c2);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
 [a 1] [b 2] [d 4]  
[a b c] == [a b c] is True  
[a b c] == [a b d] is False  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / map >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [mapy (STL/CLR)](../dotnet/map-stl-clr.md)   
 [Operator! = (map) (STL/CLR)](../dotnet/operator-inequality-map-stl-clr.md)   
 [operátor\< (map) (STL/CLR)](../dotnet/operator-less-than-map-stl-clr.md)   
 [Operator > = (map) (STL/CLR)](../dotnet/operator-greater-or-equal-map-stl-clr.md)   
 [Operator > (map) (STL/CLR)](../dotnet/operator-greater-than-map-stl-clr.md)   
 [Operator < = (map) (STL/CLR)](../dotnet/operator-less-or-equal-map-stl-clr.md)
---
title: map::Operator(STL/CLR) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::map::operator[]
dev_langs:
- C++
helpviewer_keywords:
- operatormember [] [STL/CLR]
ms.assetid: 50e494c5-62d4-4469-8da3-7432ee4dff97
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2eeedf3c6d4dda7ac8a90ac430f8d48f871750bd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33139085"
---
# <a name="mapoperatorstlclr"></a>map::Operator(STL/CLR)
Klíč se mapuje na její přidružené hodnoty namapované.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
mapped_type operator[](key_type key);  
```  
  
#### <a name="parameters"></a>Parametry  
 klíč  
 Hodnota klíče pro vyhledávání.  
  
## <a name="remarks"></a>Poznámky  
 Členské funkce záležitostí najít element s ekvivalentní řazení do `key`. V případě, že některou najde, vrátí hodnotu přiřazenou namapované; v opačném vloží `value_type(key, mapped_type())` a vrátí přidruženého namapované hodnotu (výchozí). Použijete ji najít namapované hodnotu zadané jeho přidružený klíč, nebo musí existovat položka pro klíč-li žádná nalezena.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_map_operator_sub.cpp   
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
  
    System::Console::WriteLine("c1[{0}] = {1}",   
        L'A', c1[L'A']);   
    System::Console::WriteLine("c1[{0}] = {1}",   
        L'b', c1[L'b']);   
  
// redisplay altered contents   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// alter mapped values and redisplay   
    c1[L'A'] = 10;   
    c1[L'c'] = 13;   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
c1[A] = 0  
c1[b] = 2  
 [A 0] [a 1] [b 2] [c 3]  
 [A 10] [a 1] [b 2] [c 13]  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / map >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [mapy (STL/CLR)](../dotnet/map-stl-clr.md)   
 [map::Find (STL/CLR)](../dotnet/map-find-stl-clr.md)   
 [map::insert (STL/CLR)](../dotnet/map-insert-stl-clr.md)
---
title: map::map (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::map::map
dev_langs: C++
helpviewer_keywords: map member [STL/CLR]
ms.assetid: c91f699a-4742-4859-b2b3-c2a01a750bea
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d8fe3e0dd20ae07f3378bd528d7e19986c2aed6b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="mapmap-stlclr"></a>map::map (STL/CLR)
Sestaví objekt kontejneru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
map();  
explicit map(key_compare^ pred);  
map(map<Key, Mapped>% right);  
map(map<Key, Mapped>^ right);  
template<typename InIter>  
    mapmap(InIter first, InIter last);  
template<typename InIter>  
    map(InIter first, InIter last,  
        key_compare^ pred);  
map(System::Collections::Generic::IEnumerable<GValue>^ right);  
map(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred);  
```  
  
#### <a name="parameters"></a>Parametry  
 první  
 Začátek rozsahu k vložení.  
  
 poslední  
 Konec rozsahu k vložení.  
  
 Před  
 Řazení predikát pro řízené sekvenci.  
  
 vpravo  
 Objekt, nebo rozsah k vložení.  
  
## <a name="remarks"></a>Poznámky  
 Konstruktor:  
  
 `map();`  
  
 Inicializuje výchozí řazení predikát řízené sekvenci bez prvků `key_compare()`. Se používá k určení prázdný počáteční řízené sekvenci, s výchozí řazení predikátu.  
  
 Konstruktor:  
  
 `explicit map(key_compare^ pred);`  
  
 Inicializuje řízené sekvenci bez prvků s řazení predikát `pred`. Se používá k určení prázdný počáteční řízené sekvenci, pomocí zadaného predikátu řazení.  
  
 Konstruktor:  
  
 `map(map<Key, Mapped>% right);`  
  
 Inicializuje řízené sekvenci s pořadím [`right.begin()`, `right.end()`), s výchozí řazení predikátu. Se používá k určení počáteční řízené sekvenci, který je kopií pořadí ovládaná objektem mapy `right`, s výchozí řazení predikátu.  
  
 Konstruktor:  
  
 `map(map<Key, Mapped>^ right);`  
  
 Inicializuje řízené sekvenci s pořadím [`right->begin()`, `right->end()`), s výchozí řazení predikátu. Se používá k určení počáteční řízené sekvenci, který je kopií pořadí ovládaná objektem mapy `right`, s výchozí řazení predikátu.  
  
 Konstruktor:  
  
 `template<typename InIter> map(InIter first, InIter last);`  
  
 Inicializuje řízené sekvenci s pořadím [`first`, `last`), s výchozí řazení predikátu. Použít k vytvoření řízené sekvenci kopie jiné pořadí, výchozí řazení predikátu.  
  
 Konstruktor:  
  
 `template<typename InIter> map(InIter first, InIter last, key_compare^ pred);`  
  
 Inicializuje řízené sekvenci s pořadím [`first`, `last`), s řazení predikát `pred`. Použít k vytvoření kopie jiné pořadí, pomocí zadaného predikátu řazení řízené sekvenci.  
  
 Konstruktor:  
  
 `map(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 Inicializuje řízené sekvenci s pořadím určené, které enumerátor `right`, s výchozí řazení predikátu. Použít k vytvoření kopie jiné pořadí popsaného enumerátor, s výchozí řazení predikát řízené sekvenci.  
  
 Konstruktor:  
  
 `map(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`  
  
 Inicializuje řízené sekvenci s pořadím určené, které enumerátor `right`, s řazení predikát `pred`. Použít k vytvoření kopie jiné pořadí popsaného enumerátor pomocí zadaného predikátu řazení řízené sekvenci.  
  
## <a name="example"></a>Příklad  
  
```cpp  
// cliext_map_construct.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
// construct an empty container   
    Mymap c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Mymap c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Mymap c3(c1.begin(), c1.end());   
    for each (Mymap::value_type elem in c3)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Mymap c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (Mymap::value_type elem in c4)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Mymap c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Mymap::value_type>^)%c3);   
    for each (Mymap::value_type elem in c5)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Mymap c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Mymap::value_type>^)%c3,   
                cliext::greater_equal<wchar_t>());   
    for each (Mymap::value_type elem in c6)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mymap c7(c4);   
    for each (Mymap::value_type elem in c7)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    Mymap c8(%c3);   
    for each (Mymap::value_type elem in c8)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 [a 1] [b 2] [c 3]  
size() = 0  
 [c 3] [b 2] [a 1]  
 [a 1] [b 2] [c 3]  
 [c 3] [b 2] [a 1]  
 [a 1] [b 2] [c 3]  
 [c 3] [b 2] [a 1]  
 [c 3] [b 2] [a 1]  
 [a 1] [b 2] [c 3]  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / map >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [mapy (STL/CLR)](../dotnet/map-stl-clr.md)   
 [map::generic_container (STL/CLR)](../dotnet/map-generic-container-stl-clr.md)   
 [map::Operator = (STL/CLR)](../dotnet/map-operator-assign-stl-clr.md)
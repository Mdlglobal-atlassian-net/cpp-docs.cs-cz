---
title: hash_map::Insert (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::hash_map::insert
dev_langs: C++
helpviewer_keywords: insert member [STL/CLR]
ms.assetid: 52926ec7-ad4e-4791-a043-46136ee40a69
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f50f2791a7d40f6ccc39d3fef221eeb7faa689b1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="hashmapinsert-stlclr"></a>hash_map::insert (STL/CLR)
Přidá prvky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
cliext::pair<iterator, bool> insert(value_type val);  
iterator insert(iterator where, value_type val);  
template<typename InIter>  
    void insert(InIter first, InIter last);  
void insert(System::Collections::Generic::IEnumerable<value_type>^ right);  
```  
  
#### <a name="parameters"></a>Parametry  
 první  
 Začátek rozsahu k vložení.  
  
 poslední  
 Konec rozsahu k vložení.  
  
 vpravo  
 Výčet k vložení.  
  
 Val  
 Hodnota klíče k vložení.  
  
 kde  
 Kde v kontejneru vložit (pouze pro pomocný parametr).  
  
## <a name="remarks"></a>Poznámky  
 Každý z členské funkce vloží sekvenci určeného zbývající operandy.  
  
 První člen funkce endeavors vložit element s hodnotou `val`a vrátí dvojici hodnot `X`. Pokud `X.second` má hodnotu true, `X.first` označí nově vloženou element jinak `X.first` označí element s ekvivalentní řazení, která již existuje a je vložen žádné nového elementu. Použijte k vložení jediným elementem.  
  
 Druhý členská funkce vloží element s hodnotou `val`pomocí `where` jako nápovědu (výkon) a vrátí iterátor, který označuje nově vloženou elementu. Použijte k vložení jednoho elementu, což může být přiléhající k elementu, které znáte.  
  
 Třetí členská funkce vloží sekvenci [`first`, `last`). Použijte k vložení počtu nula či více elementů zkopírovaných z jiného pořadí.  
  
 Čtvrtý – členská funkce vloží pořadí určené, které `right`. Použijte k vložení sekvenci popsaného enumerátor.  
  
 Každý element vložení trvá dobu úměrná logaritmus počet elementů v řízené sekvenci. Vložení se může objevit v amortizovaný čas konstantní však zadána nápovědu, který určuje element přiléhající k kurzor.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_hash_map_insert.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
typedef Myhash_map::pair_iter_bool Pairib;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert a single value, unique and duplicate   
    Pairib pair1 =   
        c1.insert(Myhash_map::make_value(L'x', 24));   
    System::Console::WriteLine("insert([L'x' 24]) = [{0} {1}] {2}",   
        pair1.first->first, pair1.first->second, pair1.second);   
  
    pair1 = c1.insert(Myhash_map::make_value(L'b', 2));   
    System::Console::WriteLine("insert([L'b' 2]) = [{0} {1}] {2}",   
        pair1.first->first, pair1.first->second, pair1.second);   
  
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert a single value with hint   
    Myhash_map::iterator it =   
        c1.insert(c1.begin(), Myhash_map::make_value(L'y', 25));   
    System::Console::WriteLine("insert(begin(), [L'y' 25]) = [{0} {1}]",   
        it->first, it->second);   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    Myhash_map c2;   
    it = c1.end();   
    c2.insert(c1.begin(), --it);   
    for each (Myhash_map::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    Myhash_map c3;   
    c3.insert(   // NOTE: cast is not needed   
        (System::Collections::Generic::   
            IEnumerable<Myhash_map::value_type>^)%c1);   
    for each (Myhash_map::value_type elem in c3)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
insert([L'x' 24]) = [x 24] True  
insert([L'b' 2]) = [b 2] False  
 [a 1] [b 2] [c 3] [x 24]  
insert(begin(), [L'y' 25]) = [y 25]  
 [a 1] [b 2] [c 3] [x 24] [y 25]  
 [a 1] [b 2] [c 3] [x 24]  
 [a 1] [b 2] [c 3] [x 24] [y 25]  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / hash_map >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [hash_map – (STL/CLR)](../dotnet/hash-map-stl-clr.md)
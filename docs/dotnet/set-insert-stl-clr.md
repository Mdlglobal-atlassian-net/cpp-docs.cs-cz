---
title: set::Insert (STL/CLR) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::set::insert
dev_langs:
- C++
helpviewer_keywords:
- insert member [STL/CLR]
ms.assetid: 40472869-5c28-4658-b1d3-3ede4d8b8921
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 619dab8844920f61a19c5159fc96c688cafebfdd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="setinsert-stlclr"></a>set::insert (STL/CLR)
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
// cliext_set_insert.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
typedef Myset::pair_iter_bool Pairib;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value, unique and duplicate   
    Pairib pair1 = c1.insert(L'x');   
    System::Console::WriteLine("insert(L'x') = [{0} {1}]",   
        *pair1.first, pair1.second);   
  
    pair1 = c1.insert(L'b');   
    System::Console::WriteLine("insert(L'b') = [{0} {1}]",   
        *pair1.first, pair1.second);   
  
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value with hint   
    System::Console::WriteLine("insert(begin(), L'y') = {0}",   
        *c1.insert(c1.begin(), L'y'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    Myset c2;   
    Myset::iterator it = c1.end();   
    c2.insert(c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    Myset c3;   
    c3.insert(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
insert(L'x') = [x True]  
insert(L'b') = [b False]  
 a b c x  
insert(begin(), L'y') = y  
 a b c x y  
 a b c x  
 a b c x y  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – nebo nastavení >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [set (STL/CLR)](../dotnet/set-stl-clr.md)
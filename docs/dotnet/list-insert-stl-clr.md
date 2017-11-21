---
title: list::Insert (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::list::insert
dev_langs: C++
helpviewer_keywords: insert member [STL/CLR]
ms.assetid: 399ed30f-6b76-41a8-b180-6070e3ca1c68
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d2a0fd1aad6b32de4f9232cbb7f7874255d1ecba
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="listinsert-stlclr"></a>list::insert (STL/CLR)
Přidá elementy na zadané pozici.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
iterator insert(iterator where, value_type val);  
void insert(iterator where, size_type count, value_type val);  
template<typename InIt>  
    void insert(iterator where, InIt first, InIt last);  
void insert(iterator where,  
    System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>Parametry  
 count  
 Počet elementů k vložení.  
  
 první  
 Začátek rozsahu k vložení.  
  
 poslední  
 Konec rozsahu k vložení.  
  
 vpravo  
 Výčet k vložení.  
  
 Val  
 Hodnota elementu, který chcete vložit.  
  
 kde  
 Kde v kontejneru vložit před.  
  
## <a name="remarks"></a>Poznámky  
 Každý člen funkce vložení před element, na kterou odkazuje `where` v řízené sekvenci sekvenci určeného zbývající operandy.  
  
 První člen funkce vloží element s hodnotou `val` a vrátí iterátor, který označuje nově vloženou elementu. Použijete jej vložit jeden prvek před místo určené, které iterace.  
  
 Druhý členská funkce vloží opakování `count` elementy hodnoty `val`. Použijte k vložení nula nebo více souvislý prvků, které jsou všechny kopie stejnou hodnotu.  
  
 Pokud `InIt` je typ integer třetí členská funkce se chová stejně jako `insert(where, (size_type)first, (value_type)last)`. Jinak, vloží sekvenci [`first`, `last`). Použijte k vložení nula nebo více souvislý prvků zkopírovaných z jiného pořadí.  
  
 Čtvrtý – členská funkce vloží pořadí určené, které `right`. Použijte k vložení sekvenci popsaného enumerátor.  
  
 Při vkládání jeden prvek, je počet kopií element lineární v počet elementů mezi kurzor a blíž k uživateli koncem pořadí. (Při vkládání jeden či více elementů na libovolném konci sekvenci, žádné element kopie dojít.) Pokud `InIt` je iterátor vstupní třetí členská funkce efektivně provádí jeden vložení pro každý prvek v pořadí. Jinak, při vkládání `N` elementy, je lineární v počtu kopií element `N` plus počet elementů mezi kurzor a blíž k uživateli koncem pořadí.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_list_insert.cpp   
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
  
// insert a single value using iterator   
    cliext::list<wchar_t>::iterator it = c1.begin();   
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",   
        *c1.insert(++it, L'x'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a repetition of values   
    cliext::list<wchar_t> c2;   
    c2.insert(c2.begin(), 2, L'y');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    it = c1.end();   
    c2.insert(c2.end(), c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    c2.insert(c2.begin(),   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value using index   
    it = c2.begin();   
    ++it, ++it, ++it;   
    c2.insert(it, L'z');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
insert(begin()+1, L'x') = x  
 a x b c  
 y y  
 y y a x b  
 a x b c y y a x b  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – nebo jejich výpisu >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [seznam (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list::Assign (STL/CLR)](../dotnet/list-assign-stl-clr.md)
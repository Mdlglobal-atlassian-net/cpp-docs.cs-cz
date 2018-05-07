---
title: deque::Insert (STL/CLR) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::deque::insert
dev_langs:
- C++
helpviewer_keywords:
- insert member [STL/CLR]
ms.assetid: a3b86c46-e6a8-42d0-b642-5a8f05ddd68c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6819b1c2e1086c38b2bb1be8207a26afc85168d3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="dequeinsert-stlclr"></a>deque::insert (STL/CLR)
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
 `count`  
 Počet elementů k vložení.  
  
 `first`  
 Začátek rozsahu k vložení.  
  
 `last`  
 Konec rozsahu k vložení.  
  
 `right`  
 Výčet k vložení.  
  
 `val`  
 Hodnota elementu, který chcete vložit.  
  
 `where`  
 Kde v kontejneru vložit před.  
  
## <a name="remarks"></a>Poznámky  
 Každý člen funkce vložení před element, na kterou odkazuje `where` v řízené sekvenci sekvenci určeného zbývající operandy.  
  
 První člen funkce vloží element s hodnotou `val` a vrátí iterátor, který označuje nově vloženou elementu. Použijete jej vložit jeden prvek před místo určené, které iterace.  
  
 Druhý členská funkce vloží opakování `count` elementy hodnoty `val`. Použijte k vložení nula nebo více souvislý prvků, které jsou všechny kopie stejnou hodnotu.  
  
 Pokud `InIt` je typ integer třetí členská funkce se chová stejně jako `insert(where, (size_type)first, (value_type)last)`. Jinak, vloží sekvenci [`first`, `last`). Použijte k vložení nula nebo více souvislý prvků zkopírovaných z jiného pořadí.  
  
 Čtvrtý – členská funkce vloží pořadí určené, které `right`. Použijte k vložení sekvenci popsaného enumerátor.  
  
 Při vkládání jeden prvek, je počet kopií element lineární v počet elementů mezi kurzor a blíž k uživateli koncem pořadí. (Při vkládání jeden či více elementů na libovolném konci sekvenci, žádné element kopie dojít.) Pokud `InIt` je iterátor vstupní třetí členská funkce efektivně provádí jeden vložení pro každý prvek v pořadí. Jinak, při vkládání `N` elementy, je lineární v počtu kopií element `N` plus počet elementů mezi kurzor a blíž k uživateli koncem pořadí.  
  
## <a name="example"></a>Příklad  
  
```cpp  
// cliext_deque_insert.cpp   
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
  
// insert a single value using iterator   
    cliext::deque<wchar_t>::iterator it = c1.begin();   
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",   
        *c1.insert(++it, L'x'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a repetition of values   
    cliext::deque<wchar_t> c2;   
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
 **Záhlaví:** \<cliext – / deque >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [deque::assign (STL/CLR)](../dotnet/deque-assign-stl-clr.md)
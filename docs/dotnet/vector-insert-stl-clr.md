---
title: Vector::Insert (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::vector::insert
dev_langs:
- C++
helpviewer_keywords:
- insert member [STL/CLR]
ms.assetid: f240cabf-f9d1-40c1-9cfb-975a90955546
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b330a9e0b8a11f41ceab4f604b73b93e8f1d735a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="vectorinsert-stlclr"></a>vector::insert (STL/CLR)
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
// cliext_vector_insert.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value using iterator   
    cliext::vector<wchar_t>::iterator it = c1.begin();   
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",   
        *c1.insert(++it, L'x'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a repetition of values   
    cliext::vector<wchar_t> c2;   
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
 **Záhlaví:** \<cliext – / vektoru >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [vektor (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [vector::assign (STL/CLR)](../dotnet/vector-assign-stl-clr.md)
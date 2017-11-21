---
title: list::list (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::list::list
dev_langs: C++
helpviewer_keywords: list member [STL/CLR]
ms.assetid: 51b58f63-c65a-4d54-b746-0c10635b123b
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f5ed413ec892ebdf89fc903ac9a9f06e4f2d917a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="listlist-stlclr"></a>list::list (STL/CLR)
Sestaví objekt kontejneru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
list();  
list(list<Value>% right);  
list(list<Value>^ right);  
explicit list(size_type count);  
list(size_type count, value_type val);  
template<typename InIt>  
    list(InIt first, InIt last);  
list(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>Parametry  
 `count`  
 Počet elementů k vložení.  
  
 `first`  
 Začátek rozsahu k vložení.  
  
 `last`  
 Konec rozsahu k vložení.  
  
 `right`  
 Objekt, nebo rozsah k vložení.  
  
 `val`  
 Hodnota elementu, který chcete vložit.  
  
## <a name="remarks"></a>Poznámky  
  
 Konstruktor:  
  
 `list();`  
  
 Inicializuje řízené sekvenci s žádné elementy. Se používá k určení prázdný počáteční řízené sekvenci.  
  
 Konstruktor:  
  
 `list(list<Value>% right);`  
  
 Inicializuje řízené sekvenci s pořadím [`right.begin()`, `right.end()`). Se používá k určení počáteční řízené sekvenci, který je kopií pořadí ovládaná objektem seznamu `right`.  
  
 Konstruktor:  
  
 `list(list<Value>^ right);`  
  
 Inicializuje řízené sekvenci s pořadím [`right->begin()`, `right->end()`). Se používá k určení počáteční řízené sekvenci, který je kopií pořadí řízené list objekt, jehož popisovač `right`.  
  
 Konstruktor:  
  
 `explicit list(size_type count);`  
  
 Inicializuje řízené sekvenci s `count` elementy s hodnotou `value_type()`. Použijete jej vyplníte kontejneru elementů všechny má výchozí hodnotu.  
  
 Konstruktor:  
  
 `list(size_type count, value_type val);`  
  
 Inicializuje řízené sekvenci s `count` elementy s hodnotou `val`. Použijete jej vyplníte kontejneru elementů všechny má stejnou hodnotu.  
  
 Konstruktor:  
  
 `template<typename InIt>`  
  
 `list(InIt first, InIt last);`  
  
 Inicializuje řízené sekvenci s pořadím [`first`, `last`). Použít k vytvoření kopie jiné pořadí řízené sekvenci.  
  
 Konstruktor:  
  
 `list(System::Collections::Generic::IEnumerable<Value>^ right);`  
  
 Inicializuje řízené sekvenci s pořadím určené, které enumerátor `right`. Použít k vytvoření kopie jiné pořadí popsaného enumerátor řízené sekvenci.  
  
## <a name="example"></a>Příklad  
  
```cpp  
// cliext_list_construct.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
// construct an empty container   
    cliext::list<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct with a repetition of default values   
    cliext::list<wchar_t> c2(3);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// construct with a repetition of values   
    cliext::list<wchar_t> c3(6, L'x');   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    cliext::list<wchar_t>::iterator it = c3.end();   
    cliext::list<wchar_t> c4(c3.begin(), --it);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    cliext::list<wchar_t> c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    cliext::list<wchar_t> c7(c3);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    cliext::list<wchar_t> c8(%c3);   
    for each (wchar_t elem in c8)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 0 0 0  
 x x x x x x  
 x x x x x  
 x x x x x x  
 x x x x x x  
 x x x x x x  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – nebo jejich výpisu >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [seznam (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list::Assign (STL/CLR)](../dotnet/list-assign-stl-clr.md)   
 [list::generic_container (STL/CLR)](../dotnet/list-generic-container-stl-clr.md)   
 [list::Operator = (STL/CLR)](../dotnet/list-operator-assign-stl-clr.md)
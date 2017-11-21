---
title: list::splice (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::list::splice
dev_langs: C++
helpviewer_keywords: splice member [STL/CLR]
ms.assetid: ebc424b9-8341-4a88-b101-86d56324f5ac
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9bbc7517013edd4c7af7c40c3787d8ec7749df32
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="listsplice-stlclr"></a>list::splice (STL/CLR)
Restitch propojení mezi uzly.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void splice(iterator where, list<Value>% right);  
void splice(iterator where, list<Value>% right,  
    iterator first);  
void splice(iterator where, list<Value>% right,  
    iterator first, iterator last);  
```  
  
#### <a name="parameters"></a>Parametry  
 první  
 Začátek rozsahu do splice.  
  
 poslední  
 Konec rozsahu do splice.  
  
 vpravo  
 Kontejner pro splice z.  
  
 kde  
 Kde v kontejneru na splice před.  
  
## <a name="remarks"></a>Poznámky  
 První člen funkce vloží pořadí řízené `right` před elementu v řízené sekvenci, na kterou odkazuje `where`. Také odebere všechny elementy z `right`. (`%right` nesmí být stejný jako `this`.) Použít na všechny jeden seznam splice do jiné.  
  
 Druhý členská funkce odebere element na kterou odkazuje `first` v řízené sekvenci `right` a vloží ho před elementu v řízené sekvenci na kterou odkazuje `where`. (Pokud `where` `==` `first` `||` `where` `== ++first`, žádná změna.) Použijete ho k splice jeden element jeden seznam do jiné.  
  
 Třetí členská funkce vloží Podoblast sady určené, které [`first`, `last`) z pořadí řízené `right` před elementu v řízené sekvenci, na kterou odkazuje `where`. Odebere také původní Podoblast sady z pořadí řízené `right`. (Pokud `right` `==` `this`, rozsah [`first`, `last`) nesmí obsahovat elementu, na kterou odkazuje `where`.) Použijete ho k splice dalším počtu nula či více elementů z jednoho seznamu do jiné.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_list_splice.cpp   
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
  
// splice to a new list   
    cliext::list<wchar_t> c2;   
    c2.splice(c2.begin(), c1);   
    System::Console::WriteLine("c1.size() = {0}", c1.size());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// return one element   
    c1.splice(c1.end(), c2, c2.begin());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// return remaining elements   
    c1.splice(c1.begin(), c2, c2.begin(), c2.end());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("c2.size() = {0}", c2.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
c1.size() = 0  
 a b c  
 a  
 b c  
 b c a  
c2.size() = 0  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – nebo jejich výpisu >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [seznam (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list::Assign (STL/CLR)](../dotnet/list-assign-stl-clr.md)   
 [list::Insert (STL/CLR)](../dotnet/list-insert-stl-clr.md)   
 [list::merge (STL/CLR)](../dotnet/list-merge-stl-clr.md)
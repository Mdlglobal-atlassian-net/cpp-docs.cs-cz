---
title: list::Unique (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::list::unique
dev_langs: C++
helpviewer_keywords: unique member [STL/CLR]
ms.assetid: c3a29e4e-0ec1-4472-b050-7a9511037132
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ca78fcc1de8b579a647dd9080dc64db0fde54e9b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="listunique-stlclr"></a>list::unique (STL/CLR)
Odebere přiléhající prvky, které předávají testu zadaný.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void unique();  
template<typename Pred2>  
    void unique(Pred2 pred);  
```  
  
#### <a name="parameters"></a>Parametry  
 Před  
 Porovnávače pro dvojice elementu.  
  
## <a name="remarks"></a>Poznámky  
 První člen funkce se odebere z řízené sekvenci (vymazáním) každý element, který porovnává rovno jeho předchozí element – Pokud element `X` předchází element `Y` a `X == Y`, odebere – členská funkce `Y`. Použijete jej odebrat všechny kromě jednoho kopii každé dalším přiléhající elementů tohoto porovnání rovnosti. Všimněte si, že pokud řízené sekvenci je seřadit, například jako voláním [list::sort (STL/CLR)](../dotnet/list-sort-stl-clr.md)`()`, – členská funkce ponechá pouze elementy s jedinečné hodnoty. (Proto název).  
  
 Druhý členská funkce se chová stejně jako první, s tím rozdílem, že jej odebere každý prvek `Y` následující element `X` pro kterou `pred(X, Y)`. Použijete jej odebrat všechny kromě jednoho kopii každé dalším přiléhající elementů, které vyhovují funkce predikátu nebo delegáta, který zadáte. Všimněte si, že pokud řízené sekvenci je seřadit, například jako voláním `sort(pred)`, – členská funkce ponechá pouze elementy, které nemají ekvivalentní řazení s jinými prvky.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_list_unique.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display contents after unique   
    cliext::list<wchar_t> c2(c1);   
    c2.unique();   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display contents after unique(not_equal_to)   
    c2 = c1;   
    c2.unique(cliext::not_equal_to<wchar_t>());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a a b c  
a b c  
a a  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – nebo jejich výpisu >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [seznam (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list::Remove (STL/CLR)](../dotnet/list-remove-stl-clr.md)   
 [list::remove_if (STL/CLR)](../dotnet/list-remove-if-stl-clr.md)   
 [list::sort (STL/CLR)](../dotnet/list-sort-stl-clr.md)
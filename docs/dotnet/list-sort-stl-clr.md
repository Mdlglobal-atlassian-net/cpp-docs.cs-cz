---
title: list::sort (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::list::sort
dev_langs: C++
helpviewer_keywords: sort member [STL/CLR]
ms.assetid: f811d5f4-a19e-4194-8765-1e68097c52f0
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6531459f26605aa63eccbe69c84959b2abe70493
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="listsort-stlclr"></a>list::sort (STL/CLR)
Řadí řízené sekvenci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void sort();  
template<typename Pred2>  
    void sort(Pred2 pred);  
```  
  
#### <a name="parameters"></a>Parametry  
 Před  
 Porovnávače pro dvojice elementu.  
  
## <a name="remarks"></a>Poznámky  
 První člen funkce pořadí prvků v řízené sekvenci tak, že jsou seřazené podle `operator<` – elementy nesnižujte v hodnotě v průběhu sekvenci. Používáte tuto funkci člen seřadit pořadí ve vzestupném pořadí.  
  
 Druhý členská funkce se chová stejně jako první, s tím rozdílem, že je pořadí řazení podle `pred`  --  `pred(X, Y)` je hodnota false pro libovolný element `X` element, který následuje `Y` v výsledné pořadí. Použít k seřazení pořadí, v pořadí, které zadáte funkce predikátu nebo delegáta.  
  
 Jak funkce provést stabilní řazení – žádné pár elementů v původní řízené sekvenci je obrácený v výsledné řízené sekvenci.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_list_sort.cpp   
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
  
// sort descending and redisplay   
    c1.sort(cliext::greater<wchar_t>());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// sort ascending and redisplay   
    c1.sort();   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
c b a  
a b c  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – nebo jejich výpisu >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [seznam (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list::merge (STL/CLR)](../dotnet/list-merge-stl-clr.md)   
 [list::reverse (STL/CLR)](../dotnet/list-reverse-stl-clr.md)   
 [list::splice (STL/CLR)](../dotnet/list-splice-stl-clr.md)   
 [list::Unique (STL/CLR)](../dotnet/list-unique-stl-clr.md)
---
title: list::merge (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::list::merge
dev_langs: C++
helpviewer_keywords: merge member [STL/CLR]
ms.assetid: f8e93cd3-bd08-4086-859b-08a2899cc9a6
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6547cb0a60b0e65bbfd11acd03d1d5bf7d926c86
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="listmerge-stlclr"></a>list::merge (STL/CLR)
Sloučí dvě řízené pořadí řazení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void merge(list<Value>% right);  
template<typename Pred2>  
    void merge(list<Value>% right, Pred2 pred);  
```  
  
#### <a name="parameters"></a>Parametry  
 Před  
 Porovnávače pro dvojice elementu.  
  
 vpravo  
 Kontejner sloučit v.  
  
## <a name="remarks"></a>Poznámky  
 První člen funkce odebere všechny elementy z pořadí řízené `right` a vložte je v řízené sekvenci. Obě pořadí musí být dříve seřazené podle `operator<` – elementy nesmí snížení hodnoty v průběhu buď pořadí. Výsledné pořadí je také seřazené podle `operator<`. Sloučit dva pořadí, které se zvyšují v hodnotě do sekvence, které se také zvyšuje hodnotu použijete tuto funkci člen.  
  
 Druhý členská funkce se chová stejně jako první, s tím rozdílem, že pořadí jsou seřazené podle `pred`  --  `pred(X, Y)` musí mít hodnotu false pro libovolný element `X` element, který následuje `Y` v pořadí. Použít sloučit dva pořadí řazení podle funkce predikátu nebo delegáta, který zadáte.  
  
 Jak funkce provést stabilní sloučení – žádné pár elementů v některém z původní řízené pořadí je obrácený v výsledné řízené sekvenci. Navíc pokud pár elementů `X` a `Y` v řízené sekvenci výsledné má ekvivalentní řazení – `!(X < Y) && !(X < Y)` – element z původní řízené sekvenci se zobrazuje před element z pořadí řízené `right`.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_list_merge.cpp   
// compile with: /clr   
#include <cliext/list>   
  
typedef cliext::list<wchar_t> Mylist;   
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'c');   
    c1.push_back(L'e');   
  
// display initial contents " a c e"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    cliext::list<wchar_t> c2;   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
    c2.push_back(L'f');   
  
// display initial contents " b d f"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// merge and display   
    cliext::list<wchar_t> c3(c1);   
    c3.merge(c2);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("c2.size() = {0}", c2.size());   
  
// sort descending, merge descending, and redisplay   
    c1.sort(cliext::greater<wchar_t>());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    c3.sort(cliext::greater<wchar_t>());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    c3.merge(c1, cliext::greater<wchar_t>());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("c1.size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a c e  
 b d f  
 a b c d e f  
c2.size() = 0  
 e c a  
 f e d c b a  
 f e e d c c b a a  
c1.size() = 0  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – nebo jejich výpisu >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [seznam (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list::sort (STL/CLR)](../dotnet/list-sort-stl-clr.md)   
 [list::splice (STL/CLR)](../dotnet/list-splice-stl-clr.md)
---
title: "větší (STL/CLR) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::greater
dev_langs: C++
helpviewer_keywords: greater function [STL/CLR]
ms.assetid: a6dfe5e3-b5a5-4ec4-8e53-8dd33a37d10d
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 47a2e525158d76182387f8ff82d6d0e08fd003c8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="greater-stlclr"></a>greater (STL/CLR)
Šablony třídy popisuje functor, že při volání, vrátí hodnotu true pouze v případě, že první argument je větší než druhý. Můžete ji použít, zadejte objekt funkce z hlediska jeho typ argumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Arg>  
    ref class greater  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    greater();  
    greater(greater<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Parametry  
 Arg  
 Typ argumenty.  
  
## <a name="member-functions"></a>Členské funkce  
  
|Definice typu|Popis|  
|---------------------|-----------------|  
|delegate_type|Typ obecný delegát.|  
|first_argument_type|Typ prvního argumentu functor.|  
|result_type|Typ výsledku functor.|  
|second_argument_type|Typ functor druhý argument.|  
  
|Člen|Popis|  
|------------|-----------------|  
|greater|Vytvoří functor.|  
  
|Operátor|Popis|  
|--------------|-----------------|  
|Operator() –|Vypočítá požadované funkce.|  
|operátor delegate_type ^|Vrhá functor s delegátem.|  
  
## <a name="remarks"></a>Poznámky  
 Šablony třídy popisuje dva argument functor. Definuje operátor členů `operator()` tak, aby objekt, kdy se nazývá jako funkce, vrátí hodnotu true pouze pokud první argument je větší než druhý.  
  
 Objekt můžete předat také jako argument funkce, jejíž typ je `delegate_type^` a bude odpovídajícím způsobem převést.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_greater.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c2;   
    c2.push_back(3);   
    c2.push_back(3);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 3 3"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::greater<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 3  
3 3  
1 0  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / funkční >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [less_equal – (STL/CLR)](../dotnet/less-equal-stl-clr.md)
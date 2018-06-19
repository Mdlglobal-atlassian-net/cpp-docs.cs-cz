---
title: greater_equal – (STL/CLR) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::greater_equal
dev_langs:
- C++
helpviewer_keywords:
- greater_equal function [STL/CLR]
ms.assetid: 4d4d8301-72dd-4a06-a652-5237e1e72a88
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5642fe8e4c2567d63b69fcfc5156f248e7b39bd3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33109333"
---
# <a name="greaterequal-stlclr"></a>greater_equal (STL/CLR)
Šablony třídy popisuje functor, při volání, vrátí hodnotu true pouze pokud první argument je větší než nebo rovna hodnotě druhý. Můžete ji použít, zadejte objekt funkce z hlediska jeho typ argumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Arg>  
    ref class greater_equal  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    greater_equal();  
    greater_equal(greater_equal<Arg>% right);  
  
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
|greater_equal|Vytvoří functor.|  
  
|Operátor|Popis|  
|--------------|-----------------|  
|Operator() –|Vypočítá požadované funkce.|  
|operátor delegate_type ^|Vrhá functor s delegátem.|  
  
## <a name="remarks"></a>Poznámky  
 Šablony třídy popisuje dva argument functor. Definuje operátor členů `operator()` tak, aby objekt, kdy se nazývá jako funkce, vrátí hodnotu true pouze pokud první argument je větší než nebo rovna hodnotě druhý.  
  
 Objekt můžete předat také jako argument funkce, jejíž typ je `delegate_type^` a bude odpovídajícím způsobem převést.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_greater_equal.cpp   
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
    c2.push_back(4);   
    c2.push_back(4);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 4 4"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::greater_equal<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 3  
4 4  
1 0  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / funkční >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [less (STL/CLR)](../dotnet/less-stl-clr.md)
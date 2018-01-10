---
title: "rozdělí (STL/CLR) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::divides
dev_langs: C++
helpviewer_keywords: divides function [STL/CLR]
ms.assetid: 4c36026a-02ba-475d-af68-854599647f4b
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b634b9e0d04575d17936d9dd855dfab4d8f13c16
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="divides-stlclr"></a>divides (STL/CLR)
Šablony třídy popisuje functor, při volání, vrátí první argument rozdělené druhou. Můžete ji použít, zadejte objekt funkce z hlediska jeho typ argumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Arg>  
    ref class divides  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef Arg result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    divides();  
    divides(divides<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Parametry  
 Arg  
 Typ argumentů a návratovou hodnotu.  
  
## <a name="member-functions"></a>Členské funkce  
  
|Definice typu|Popis|  
|---------------------|-----------------|  
|delegate_type|Typ obecný delegát.|  
|first_argument_type|Typ prvního argumentu functor.|  
|result_type|Typ výsledku functor.|  
|second_argument_type|Typ functor druhý argument.|  
  
|Člen|Popis|  
|------------|-----------------|  
|divides|Vytvoří functor.|  
  
|Operátor|Popis|  
|--------------|-----------------|  
|Operator() –|Vypočítá požadované funkce.|  
|delegate_type^() – operátor|Vrhá functor s delegátem.|  
  
## <a name="remarks"></a>Poznámky  
 Šablony třídy popisuje dva argument functor. Definuje operátor členů `operator()` tak, aby objekt, kdy se nazývá jako funkce, vrátí první argument rozdělené druhou.  
  
 Objekt můžete předat také jako argument funkce, jejíž typ je `delegate_type^` a bude odpovídajícím způsobem převést.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_divides.cpp   
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
    c2.push_back(2);   
    c2.push_back(1);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 2 1"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::divides<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 3  
2 1  
2 3  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / funkční >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [numerického zbytku (STL/CLR)](../dotnet/modulus-stl-clr.md)   
 [multiplies (STL/CLR)](../dotnet/multiplies-stl-clr.md)
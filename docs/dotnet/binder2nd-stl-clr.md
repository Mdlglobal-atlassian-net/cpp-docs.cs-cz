---
title: binder2nd (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::binder2nd
dev_langs: C++
helpviewer_keywords: binder2nd function [STL/CLR]
ms.assetid: f4be8722-1778-4cb9-9ec7-ad1443f6899f
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b22c435952602afe96a7f310b931bda8a5bbb13c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="binder2nd-stlclr"></a>binder2nd (STL/CLR)
Šablony třídy popisuje functor jeden argument, pokud je volána, vrátí jeho uložené dva argument functor volána s zadaný první argument a jeho uložené druhý argument. Můžete ji použít, zadejte objekt funkce z hlediska jeho uložené functor.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Fun>  
    ref class binder2nd  
    { // wrap operator()  
public:  
    typedef Fun stored_function_type;  
    typedef typename Fun::first_argument_type first_argument_type;  
    typedef typename Fun::second_argument_type second_argument_type;  
    typedef typename Fun:result_type result_type;  
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<  
        first_argument_type, result_type>  
        delegate_type;  
  
    binder2nd(Fun% functor, second_argument_type left);  
    binder2nd(binder2nd<Arg>% right);  
  
    result_type operator()(first_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Parametry  
 Fun  
 Typ uložené functor.  
  
## <a name="member-functions"></a>Členské funkce  
  
|Definice typu|Popis|  
|---------------------|-----------------|  
|delegate_type|Typ obecný delegát.|  
|first_argument_type|Typ prvního argumentu functor.|  
|result_type|Typ výsledku functor.|  
|second_argument_type|Typ functor druhý argument.|  
|stored_function_type|Typ functor.|  
  
|Člen|Popis|  
|------------|-----------------|  
|binder2nd|Vytvoří functor.|  
  
|Operátor|Popis|  
|--------------|-----------------|  
|Operator() –|Vypočítá požadované funkce.|  
|delegate_type^() – operátor|Vrhá functor s delegátem.|  
  
## <a name="remarks"></a>Poznámky  
 Šablony třídy popisuje functor jeden argument, který ukládá dvě argument functor a druhý argument. Definuje operátor členů `operator()` tak, aby objekt, kdy se nazývá jako funkce, vrátí výsledek volání uložené functor s zadaný první argument a uložené druhý argument.  
  
 Objekt můžete předat také jako argument funkce, jejíž typ je `delegate_type^` a bude odpovídajícím způsobem převést.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_binder2nd.cpp   
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
    Myvector c3(2, 0);   
  
// display initial contents " 4 3"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::minus<int> sub_op;   
    cliext::binder2nd<cliext::minus<int> > sub4(sub_op, 4);   
  
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        sub4);   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        bind2nd(sub_op, 4));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 3  
0 -1  
0 -1  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / funkční >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [bind2nd (STL/CLR)](../dotnet/bind2nd-stl-clr.md)
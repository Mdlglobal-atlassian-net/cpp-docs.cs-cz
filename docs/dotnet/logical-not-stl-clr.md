---
title: logical_not – (STL/CLR) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::logical_not
dev_langs:
- C++
helpviewer_keywords:
- logical_not function [STL/CLR]
ms.assetid: 32a2c6e2-1c58-41ac-8827-f3ee5adfe81d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d4048c642a1c562237bccba8fa3e5fd5429bba4e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33134224"
---
# <a name="logicalnot-stlclr"></a>logical_not (STL/CLR)
Šablony třídy popisuje functor, že při volání, vrátí hodnotu true, pouze pokud buď testy její argument jako false. Můžete ji použít, zadejte objekt funkce z hlediska jeho typ argumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Arg>  
    ref class logical_not  
    { // wrap operator()  
public:  
    typedef Arg argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<  
        argument_type, result_type>  
        delegate_type;  
  
    logical_not();  
    logical_not(logical_not<Arg> %right);  
  
    result_type operator()(argument_type left);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Parametry  
 Arg  
 Typ argumenty.  
  
## <a name="member-functions"></a>Členské funkce  
  
|Definice typu|Popis|  
|---------------------|-----------------|  
|argument_type|Typ argumentu functor.|  
|delegate_type|Typ obecný delegát.|  
|result_type|Typ výsledku functor.|  
  
|Člen|Popis|  
|------------|-----------------|  
|logical_not|Vytvoří functor.|  
  
|Operátor|Popis|  
|--------------|-----------------|  
|Operator() –|Vypočítá požadované funkce.|  
|operátor delegate_type ^|Vrhá functor s delegátem.|  
  
## <a name="remarks"></a>Poznámky  
 Šablony třídy popisuje functor jeden argument. Definuje operátor členů `operator()` tak, aby objekt, kdy se nazývá jako funkce, vrátí hodnotu true pouze pokud testy její argument jako false.  
  
 Objekt můžete předat také jako argument funkce, jejíž typ je `delegate_type^` a bude odpovídajícím způsobem převést.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_logical_not.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(0);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 0"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c3.begin(), cliext::logical_not<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 0  
0 1  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / funkční >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [negate (STL/CLR)](../dotnet/negate-stl-clr.md)
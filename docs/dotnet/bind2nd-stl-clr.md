---
title: "bind2nd – (STL/CLR) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::bind2nd
dev_langs: C++
helpviewer_keywords: bind2nd function [STL/CLR]
ms.assetid: 457cebea-38e4-4466-a468-fe9eb138e80c
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 484430c181e13508daa4936f29d078829ddda083
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="bind2nd-stlclr"></a>bind2nd (STL/CLR)
Generuje `binder2nd` argument a functor.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Fun,  
    typename Arg>  
    binder2nd<Fun> bind2nd(Fun% functor,  
        Arg right);  
```  
  
## <a name="template-parameters"></a>Parametry šablony  
 Arg  
 Typ argumentu.  
  
 Fun  
 Typ functor.  
  
## <a name="function-parameters"></a>Funkční parametry  
 functor  
 Functor zabalit.  
  
 vpravo  
 Druhý argument zabalit.  
  
## <a name="remarks"></a>Poznámky  
 Funkce šablony vrátí [binder2nd (STL/CLR)](../dotnet/binder2nd-stl-clr.md)`<Fun>(functor, right)`. Můžete ho použít jako pohodlný způsob, jak zabalit dva argument functor a její druhý parametr v functor jeden argument, který volá s prvním argumentem.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_bind2nd.cpp   
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
 [binder2nd (STL/CLR)](../dotnet/binder2nd-stl-clr.md)
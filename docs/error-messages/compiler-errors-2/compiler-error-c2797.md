---
title: "Chyba kompilátoru C2797 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2797
dev_langs: C++
helpviewer_keywords: C2797
ms.assetid: 9fb26d35-eb5c-46fc-9ff5-756fba5bdaff
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0c8fd31905eb92db8ad2e3af941772584f6f64ce
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2797"></a>Chyba kompilátoru C2797
(Zastaralé) Inicializace seznamu uvnitř inicializátoru seznamu členů nebo data nestatické členské inicializátoru není implementována.  
  
 Toto upozornění je zastaralé v sadě Visual Studio 2015. Kompilátor Visual C++ v sadě Visual Studio 2013 a starší verze, neimplementuje Inicializace seznamu uvnitř inicializátoru seznamu člen nebo inicializátoru data nestatické členské. Před Visual Studio 2013 Update 3 Tento byl se bezobslužně převeden na volání funkce, které může vést k generování chybného kódu. Visual Studio 2013 Update 3 hlásí to za chybu.  
  
 Tento příklad vytvoří C2797:  
  
```  
#include <vector>  
struct S {  
    S() : v1{1} {} // C2797, VS2013 RTM incorrectly calls 'vector(size_type)'  
  
    std::vector<int> v1;  
    std::vector<int> v2{1, 2}; // C2797, VS2013 RTM incorrectly calls 'vector(size_type, const int &)'  
};  
  
```  
  
 Tento příklad vytvoří také C2797:  
  
```  
struct S1 {  
    int i;  
};  
  
struct S2 {  
    S2() : s1{0} {} // C2797, VS2013 RTM interprets as S2() : s1(0) {} causing C2664  
    S1 s1;  
    S1 s2{0}; // C2797, VS2013 RTM interprets as S1 s2 = S1(0); causing C2664  
};  
  
```  
  
 Chcete-li tento problém vyřešit, můžete použít explicitní konstrukce vnitřní seznamů. Příklad:  
  
```  
#include <vector>  
typedef std::vector<int> Vector;  
struct S {  
    S() : v1(Vector{1}) {}  
  
    Vector v1;  
    Vector v2 = Vector{1, 2};  
};  
  
```  
  
 Pokud nechcete, aby Inicializace seznamu:  
  
```  
struct S {  
    S() : s1("") {}  
  
    std::string s1;  
    std::string s2 = std::string("");  
};  
  
```  
  
 (Kompilátor v sadě Visual Studio 2013 tomu implicitně před Visual Studio 2013 Update 3.)
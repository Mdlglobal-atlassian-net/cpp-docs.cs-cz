---
title: Vector::Erase (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::vector::erase
dev_langs: C++
helpviewer_keywords: erase member [STL/CLR]
ms.assetid: 624905eb-83c0-499b-a07a-c10aebd7acc3
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f6f0b8fcef4715355038c3eaca88ee9c69b3375c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="vectorerase-stlclr"></a>vector::erase (STL/CLR)
Odebere prvky v určených pozicích.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
```  
  
#### <a name="parameters"></a>Parametry  
 první  
 Začátek rozsahu vymazat.  
  
 poslední  
 Konec rozsahu vymazat.  
  
 kde  
 Element vymazat.  
  
## <a name="remarks"></a>Poznámky  
 Odebere první členská funkce elementu řízené sekvenci, na kterou odkazuje `where`. Použijte k odebrání jediným elementem.  
  
 Druhý členská funkce odebere elementy řízené sekvenci v rozsahu [`first`, `last`). Použijte k odebrání nula nebo více souvislý prvků.  
  
 Obě členské funkce vrátí iterátor, který označí první prvek zbývající nad rámec všechny elementy odebrán, nebo [vector::end (STL/CLR)](../dotnet/vector-end-stl-clr.md) `()` Pokud neexistuje žádný takový prvek.  
  
 Při mazání elementy, je počet kopií element lineární v počet elementů mezi koncem vymazání a blíž k uživateli konci pořadí. (Pokud mazání jeden či více elementů na libovolném konci sekvenci, žádné element kopie dojít k.)  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_vector_erase.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase an element and reinspect   
    System::Console::WriteLine("erase(begin()) = {0}",   
        *c1.erase(c1.begin()));   
  
// add elements and display " b c d e"   
    c1.push_back(L'd');   
    c1.push_back(L'e');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase all but end   
    cliext::vector<wchar_t>::iterator it = c1.end();   
    System::Console::WriteLine("erase(begin(), end()-1) = {0}",   
        *c1.erase(c1.begin(), --it));   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
erase(begin()) = b  
 b c d e  
erase(begin(), end()-1) = e  
size() = 1  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / vektoru >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [vektor (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [vector::clear (STL/CLR)](../dotnet/vector-clear-stl-clr.md)
---
title: multimap::Erase (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::multimap::erase
dev_langs: C++
helpviewer_keywords: erase member [STL/CLR]
ms.assetid: 94623cfc-4464-44a6-afd4-90a36828ac2b
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3e20432f603f1bd68749ad31d2e74abc333db48f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="multimaperase-stlclr"></a>multimap::erase (STL/CLR)
Odebere prvky v určených pozicích.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
bool erase(key_type key)  
```  
  
#### <a name="parameters"></a>Parametry  
 první  
 Začátek rozsahu vymazat.  
  
 klíč  
 Hodnota klíče vymazat.  
  
 poslední  
 Konec rozsahu vymazat.  
  
 kde  
 Element vymazat.  
  
## <a name="remarks"></a>Poznámky  
 Odebere první členská funkce elementu řízené sekvenci, na kterou odkazuje `where`a vrátí iterátor, který označí první prvek zbývající nad rámec element odebrán, nebo [multimap::end (STL/CLR)](../dotnet/multimap-end-stl-clr.md) `()` Pokud neexistuje žádný takový prvek. Použijte k odebrání jediným elementem.  
  
 Druhý členská funkce odebere elementy řízené sekvenci v rozsahu [`first`, `last`) a vrátí iterátor, který označí první prvek zbývající nad rámec všechny elementy odebrán, nebo `end()` Pokud žádný takový prvek existuje... Použijte k odebrání nula nebo více souvislý prvků.  
  
 Třetí členská funkce odebere libovolného elementu řízené sekvenci, jehož klíč má ekvivalentní řazení do `key`a vrátí počet prvků odebrat. Použijete jej odeberte a počet všechny elementy, které odpovídají zadaným klíčem.  
  
 Každý element vymazání trvá dobu úměrná logaritmus počet elementů v řízené sekvenci.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_multimap_erase.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::multimap<wchar_t, int> Mymultimap;   
int main()   
    {   
    cliext::multimap<wchar_t, int> c1;   
    c1.insert(cliext::multimap<wchar_t, int>::make_value(L'a', 1));   
    c1.insert(cliext::multimap<wchar_t, int>::make_value(L'b', 2));   
    c1.insert(cliext::multimap<wchar_t, int>::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (cliext::multimap<wchar_t, int>::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// erase an element and reinspect   
    cliext::multimap<wchar_t, int>::iterator it =   
        c1.erase(c1.begin());   
    System::Console::WriteLine("erase(begin()) = [{0} {1}]",   
        it->first, it->second);   
  
// add elements and display " b c d e"   
    c1.insert(cliext::multimap<wchar_t, int>::make_value(L'd', 4));   
    c1.insert(cliext::multimap<wchar_t, int>::make_value(L'e', 5));   
    for each (cliext::multimap<wchar_t, int>::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// erase all but end   
    it = c1.end();   
    it = c1.erase(c1.begin(), --it);   
    System::Console::WriteLine("erase(begin(), end()-1) = [{0} {1}]",   
        it->first, it->second);   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// erase end   
    System::Console::WriteLine("erase(L'x') = {0}", c1.erase(L'x'));   
    System::Console::WriteLine("erase(L'e') = {0}", c1.erase(L'e'));   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
erase(begin()) = [b 2]  
 [b 2] [c 3] [d 4] [e 5]  
erase(begin(), end()-1) = [e 5]  
size() = 1  
erase(L'x') = 0  
erase(L'e') = 1  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / map >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [multimap (STL/CLR)](../dotnet/multimap-stl-clr.md)   
 [multimap::clear (STL/CLR)](../dotnet/multimap-clear-stl-clr.md)
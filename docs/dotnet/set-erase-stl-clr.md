---
title: set::Erase (STL/CLR) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::set::erase
dev_langs:
- C++
helpviewer_keywords:
- erase member [STL/CLR]
ms.assetid: 0596514b-d4cd-4d2d-8223-3bee6980261c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 28a7f36c2ea231fcc19845976afd72f07cf0b07a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="seterase-stlclr"></a>set::erase (STL/CLR)
Odebere prvky v určených pozicích.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
size_type erase(key_type key)  
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
 Odebere první členská funkce elementu řízené sekvenci, na kterou odkazuje `where`a vrátí iterátor, který označí první prvek zbývající nad rámec element odebrán, nebo [set::end (STL/CLR)](../dotnet/set-end-stl-clr.md) `()` Pokud neexistuje žádný takový prvek. Použijte k odebrání jediným elementem.  
  
 Druhý členská funkce odebere elementy řízené sekvenci v rozsahu [`first`, `last`) a vrátí iterátor, který označí první prvek zbývající nad rámec všechny elementy odebrán, nebo `end()` Pokud žádný takový prvek existuje... Použijte k odebrání nula nebo více souvislý prvků.  
  
 Třetí členská funkce odebere libovolného elementu řízené sekvenci, jehož klíč má ekvivalentní řazení do `key`a vrátí počet prvků odebrat. Použijete jej odeberte a počet všechny elementy, které odpovídají zadaným klíčem.  
  
 Každý element vymazání trvá dobu úměrná logaritmus počet elementů v řízené sekvenci.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_set_erase.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase an element and reinspect   
    System::Console::WriteLine("erase(begin()) = {0}",   
        *c1.erase(c1.begin()));   
  
// add elements and display " b c d e"   
    c1.insert(L'd');   
    c1.insert(L'e');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase all but end   
    Myset::iterator it = c1.end();   
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
 **Záhlaví:** \<cliext – nebo nastavení >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [Sada (STL/CLR)](../dotnet/set-stl-clr.md)   
 [set::clear (STL/CLR)](../dotnet/set-clear-stl-clr.md)
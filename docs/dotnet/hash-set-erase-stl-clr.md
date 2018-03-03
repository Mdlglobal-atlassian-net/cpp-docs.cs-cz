---
title: hash_set::Erase (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::hash_set::erase
dev_langs:
- C++
helpviewer_keywords:
- erase member [STL/CLR]
ms.assetid: 620998a0-00c9-4be6-899b-2d71661375b6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 47848599b844eb45da0d30c9b410e06f51ccb63e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="hashseterase-stlclr"></a>hash_set::erase (STL/CLR)
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
 Odebere první členská funkce elementu řízené sekvenci, na kterou odkazuje `where`a vrátí iterátor, který označí první prvek zbývající nad rámec element odebrán, nebo [hash_set::end (STL/CLR)](../dotnet/hash-set-end-stl-clr.md) `()` Pokud neexistuje žádný takový prvek. Použijte k odebrání jediným elementem.  
  
 Druhý členská funkce odebere elementy řízené sekvenci v rozsahu [`first`, `last`) a vrátí iterátor, který označí první prvek zbývající nad rámec všechny elementy odebrán, nebo `end()` Pokud žádný takový prvek existuje... Použijte k odebrání nula nebo více souvislý prvků.  
  
 Třetí členská funkce odebere libovolného elementu řízené sekvenci, jehož klíč má ekvivalentní řazení do `key`a vrátí počet prvků odebrat. Použijete jej odeberte a počet všechny elementy, které odpovídají zadaným klíčem.  
  
 Každý element vymazání trvá dobu úměrná logaritmus počet elementů v řízené sekvenci.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_hash_set_erase.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
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
    Myhash_set::iterator it = c1.end();   
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
 **Záhlaví:** \<cliext – / hash_set >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [hash_set::clear (STL/CLR)](../dotnet/hash-set-clear-stl-clr.md)
---
title: hash_multiset::iterator (STL/CLR) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_multiset::iterator
dev_langs:
- C++
helpviewer_keywords:
- iterator member [STL/CLR]
ms.assetid: 47c565d9-2bbc-45d8-801f-cab43ed45ab4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7d541e9c3f9a829c6a870f9f763d4e24d597e408
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33127468"
---
# <a name="hashmultisetiterator-stlclr"></a>hash_multiset::iterator (STL/CLR)
Typ iterátoru řízené sekvence  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef T1 iterator;  
```  
  
## <a name="remarks"></a>Poznámky  
 Popisuje typ objekt neurčeného typu `T1` , může sloužit jako obousměrný iterator pro řízené sekvenci.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_hash_multiset_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    Myhash_multiset::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / hash_set >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_multiset::const_iterator (STL/CLR)](../dotnet/hash-multiset-const-iterator-stl-clr.md)
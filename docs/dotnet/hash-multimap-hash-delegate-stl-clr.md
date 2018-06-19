---
title: hash_multimap::hash_delegate (STL/CLR) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_multimap::hash_delegate
dev_langs:
- C++
helpviewer_keywords:
- hash_delegate member [STL/CLR]
ms.assetid: 2a459f6d-9bb1-4b03-a013-0998ba842c25
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c9fabb2c413abe76b1e2d60ec2753b1915bea374
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33112248"
---
# <a name="hashmultimaphashdelegate-stlclr"></a>hash_multimap::hash_delegate (STL/CLR)
Vyhledá prvek, který odpovídá zadanému klíči.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
hasher^ hash_delegate();  
```  
  
## <a name="remarks"></a>Poznámky  
 Členská funkce vrátí delegáta použitý k převedení hodnotou klíče na celé číslo. Použijte hodnoty hash klíče.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_hash_multimap_hash_delegate.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_multimap<wchar_t, int> Myhash_multimap;   
int main()   
    {   
    Myhash_multimap c1;   
    Myhash_multimap::hasher^ myhash = c1.hash_delegate();   
  
    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));   
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));   
    return (0);   
    }  
  
```  
  
```Output  
hash(L'a') = 1616896120  
hash(L'b') = 570892832  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / hash_map >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [hash_multimap (STL/CLR)](../dotnet/hash-multimap-stl-clr.md)   
 [hash_multimap::hasher (STL/CLR)](../dotnet/hash-multimap-hasher-stl-clr.md)
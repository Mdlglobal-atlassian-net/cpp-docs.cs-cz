---
title: hash_map::max_load_factor (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::hash_map::max_load_factor
dev_langs: C++
helpviewer_keywords: max_load_factor member [STL/CLR]
ms.assetid: 7c0773c9-a918-4e61-ae95-e45148f1ff24
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e9dab1452d736d85bdf029608516465fefef7997
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="hashmapmaxloadfactor-stlclr"></a>hash_map::max_load_factor (STL/CLR)
Získá nebo nastaví maximální počet prvků na kbelík.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
float max_load_factor();  
void max_load_factor(float new_factor);  
```  
  
#### <a name="parameters"></a>Parametry  
 new_factor  
 Nové maximální načíst faktor, který chcete uložit.  
  
## <a name="remarks"></a>Poznámky  
 První člen funkce vrátí aktuální Multi-Factor uložené maximální zatížení. Můžete použít k určení velikosti maximální průměrná sady.  
  
 Druhý členská funkce nahrazuje faktory maximální zatížení úložiště s `new_factor`. Žádné automatické rehashing nastane, dokud následné vložení.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_hash_map_max_load_factor.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1 = gcnew Myhash_map;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// inspect current parameters   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    System::Console::WriteLine();   
  
// change max_load_factor and redisplay   
    c1.max_load_factor(0.25f);   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    System::Console::WriteLine();   
  
// rehash and redisplay   
    c1.rehash(100);   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
bucket_count() = 16  
load_factor() = 0.1875  
max_load_factor() = 4  
  
bucket_count() = 16  
load_factor() = 0.1875  
max_load_factor() = 0.25  
  
bucket_count() = 128  
load_factor() = 0.0234375  
max_load_factor() = 0.25  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / hash_map >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [hash_map – (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_map::bucket_count (STL/CLR)](../dotnet/hash-map-bucket-count-stl-clr.md)   
 [hash_map::load_factor (STL/CLR)](../dotnet/hash-map-load-factor-stl-clr.md)   
 [hash_map::rehash (STL/CLR)](../dotnet/hash-map-rehash-stl-clr.md)
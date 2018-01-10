---
title: hash_set::make_value (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::hash_set::make_value
dev_langs: C++
helpviewer_keywords: make_value member [STL/CLR]
ms.assetid: 19819fee-d3a0-428d-92db-cba7235d37d4
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 12b9337ce1dacbeaa6e5f7ff23d90a738a53872d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="hashsetmakevalue-stlclr"></a>hash_set::make_value (STL/CLR)
Vytvoří objekt hodnoty.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
static value_type make_value(key_type key);  
```  
  
#### <a name="parameters"></a>Parametry  
 klíč  
 Hodnota klíče k použití.  
  
## <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu `value_type` objekt, jehož klíč je `key`. Použitím ji k vytvoření objektu vhodný pro použití s několik dalších členské funkce.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_hash_set_make_value.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(Myhash_set::make_value(L'a'));   
    c1.insert(Myhash_set::make_value(L'b'));   
    c1.insert(Myhash_set::make_value(L'c'));   
  
// display contents " a b c"   
    for each (Myhash_set::value_type elem in c1)   
        System::Console::Write(" {0}", elem);   
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
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [hash_set::key_type (STL/CLR)](../dotnet/hash-set-key-type-stl-clr.md)   
 [hash_set::value_type (STL/CLR)](../dotnet/hash-set-value-type-stl-clr.md)
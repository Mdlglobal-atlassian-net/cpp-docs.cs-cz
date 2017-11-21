---
title: set::make_value (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::set::make_value
dev_langs: C++
helpviewer_keywords: make_value member [STL/CLR]
ms.assetid: 2f71515e-7de1-4139-a68e-72ff2a96aa4a
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: dfa2c7af49ce367a20f8a1781ed247f21e0d8919
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="setmakevalue-stlclr"></a>set::make_value (STL/CLR)
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
// cliext_set_make_value.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(Myset::make_value(L'a'));   
    c1.insert(Myset::make_value(L'b'));   
    c1.insert(Myset::make_value(L'c'));   
  
// display contents " a b c"   
    for each (Myset::value_type elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – nebo nastavení >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [Sada (STL/CLR)](../dotnet/set-stl-clr.md)   
 [set::key_type (STL/CLR)](../dotnet/set-key-type-stl-clr.md)   
 [set::value_type (STL/CLR)](../dotnet/set-value-type-stl-clr.md)
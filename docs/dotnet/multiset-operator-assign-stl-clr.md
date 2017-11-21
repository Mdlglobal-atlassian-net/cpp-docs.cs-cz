---
title: multiset::Operator = (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::multiset::operator=
dev_langs: C++
helpviewer_keywords: operator= member [STL/CLR]
ms.assetid: 74e60042-d0d6-471f-8fdb-79b3c6856440
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1339d26047e65a5a509ab1a17295de5928f38f3d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="multisetoperator-stlclr"></a>multiset::operator= (STL/CLR)
Nahradí řízené sekvenci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
multiset<Key>% operator=(multiset<Key>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 vpravo  
 Kontejner pro kopírování.  
  
## <a name="remarks"></a>Poznámky  
 Kopie operátor člen `right` k objektu, vrátí `*this`. Můžete použít k nahrazení řízené sekvenci kopii v řízené sekvenci `right`.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_multiset_operator_as.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (Mymultiset::value_type elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymultiset c2;   
    c2 = c1;   
// display contents " a b c"   
    for each (Mymultiset::value_type elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – nebo nastavení >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [multiset (STL/CLR)](../dotnet/multiset-stl-clr.md)
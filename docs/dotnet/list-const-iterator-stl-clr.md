---
title: list::const_iterator (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::list::const_iterator
dev_langs: C++
helpviewer_keywords: const_iterator member [STL/CLR]
ms.assetid: 24e19077-02d2-456e-a3f1-7caaf0b6c974
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 76e59007b1ed45e01310795f7ada35576a57bb60
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="listconstiterator-stlclr"></a>list::const_iterator (STL/CLR)
Typ konstantního iterátoru řízené sekvence  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef T2 const_iterator;  
```  
  
## <a name="remarks"></a>Poznámky  
 Popisuje typ objekt neurčeného typu `T2` , může sloužit jako konstantní iterator náhodný přístup pro řízené sekvenci.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_list_const_iterator.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    cliext::list<wchar_t>::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        System::Console::Write(" {0}", *cit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – nebo jejich výpisu >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [seznam (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list::iterator (STL/CLR)](../dotnet/list-iterator-stl-clr.md)
---
title: Queue::Operator = (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::queue::operator=
dev_langs: C++
helpviewer_keywords: operator= member [STL/CLR]
ms.assetid: 826c335a-5680-498c-b57d-e7bc93a914be
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 558a96726e8d6ab6921e40847bc6856952c36c7b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="queueoperator-stlclr"></a>queue::operator= (STL/CLR)
Nahradí řízené sekvenci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
queue <Value, Container>% operator=(queue <Value, Container>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 vpravo  
 Kontejner adaptér pro kopírování.  
  
## <a name="remarks"></a>Poznámky  
 Kopie operátor člen `right` k objektu, vrátí `*this`. Můžete použít k nahrazení řízené sekvenci kopii v řízené sekvenci `right`.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_queue_operator_as.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myqueue c2;   
    c2 = c1;   
    for each (wchar_t elem in c2.get_container())   
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
 **Záhlaví:** \<cliext – / fronty >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [fronty (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [Queue::Assign (STL/CLR)](../dotnet/queue-assign-stl-clr.md)
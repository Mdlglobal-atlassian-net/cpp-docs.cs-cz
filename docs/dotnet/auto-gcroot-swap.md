---
title: auto_gcroot::swap | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- msclr.auto_gcroot.swap
- msclr::auto_gcroot::swap
- auto_gcroot::swap
- auto_gcroot.swap
dev_langs: C++
helpviewer_keywords: auto_gcroot::swap
ms.assetid: 4915c629-6a53-432c-8155-3a7511dc70cb
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3f3876550ed48c0ab570220042b64ccadc4cff33
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="autogcrootswap"></a>auto_gcroot::swap
Prohození objekty s jinou `auto_gcroot`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void swap(  
   auto_gcroot<_element_type> & _right  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `_right`  
 `auto_gcroot` Ke které chcete Prohodit objekty.  
  
## <a name="example"></a>Příklad  
  
```  
// msl_auto_gcroot_swap.cpp  
// compile with: /clr  
#include <msclr\auto_gcroot.h>  
  
using namespace System;  
using namespace msclr;  
  
int main() {  
   auto_gcroot<String^> s1 = "string one";  
   auto_gcroot<String^> s2 = "string two";  
  
   Console::WriteLine( "s1 = '{0}', s2 = '{1}'",  
      s1->ToString(), s2->ToString() );  
   s1.swap( s2 );  
   Console::WriteLine( "s1 = '{0}', s2 = '{1}'",  
      s1->ToString(), s2->ToString() );  
}  
```  
  
```Output  
s1 = 'string one', s2 = 'string two'  
s1 = 'string two', s2 = 'string one'  
```  
  
## <a name="requirements"></a>Požadavky  
 **Soubor hlaviček** \<msclr\auto_gcroot.h >  
  
 **Namespace** msclr –  
  
## <a name="see-also"></a>Viz také  
 [auto_gcroot – členové](../dotnet/auto-gcroot-members.md)   
 [swap – funkce (auto_gcroot)](../dotnet/swap-function-auto-gcroot.md)
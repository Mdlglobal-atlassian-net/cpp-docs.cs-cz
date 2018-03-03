---
title: auto_handle::Operator bool | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- auto_handle.operator bool
- msclr.auto_handle.operator bool
- operator bool
- msclr::auto_handle::operator bool
- auto_handle::operator bool
dev_langs:
- C++
helpviewer_keywords:
- auto_handle::operator bool
ms.assetid: 2e535e99-cf87-4008-b588-02c587d77453
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4108baa84028c4168d2c08557b9837fa845facb8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="autohandleoperator-bool"></a>auto_handle::operator bool
Operátor pro používání `auto_handle` podmíněného výrazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
operator bool();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`Pokud je objekt zabalené platný; `false` jinak.  
  
## <a name="remarks"></a>Poznámky  
 Tento operátor. ve skutečnosti převede na `_detail_class::_safe_bool` což je bezpečnější než `bool` vzhledem k tomu, že ho nelze převést na typ integrální.  
  
## <a name="example"></a>Příklad  
  
```  
// msl_auto_handle_operator_bool.cpp  
// compile with: /clr  
#include <msclr\auto_handle.h>  
  
using namespace System;  
using namespace msclr;  
  
int main() {  
   auto_handle<String> s1;  
   auto_handle<String> s2 = "hi";  
   if ( s1 ) Console::WriteLine( "s1 is valid" );  
   if ( !s1 ) Console::WriteLine( "s1 is invalid" );  
   if ( s2 ) Console::WriteLine( "s2 is valid" );  
   if ( !s2 ) Console::WriteLine( "s2 is invalid" );  
   s2.reset();  
   if ( s2 ) Console::WriteLine( "s2 is now valid" );  
   if ( !s2 ) Console::WriteLine( "s2 is now invalid" );  
}  
```  
  
```Output  
s1 is invalid  
s2 is valid  
s2 is now invalid  
```  
  
## <a name="requirements"></a>Požadavky  
 **Soubor hlaviček** \<msclr\auto_handle.h >  
  
 **Namespace** msclr –  
  
## <a name="see-also"></a>Viz také  
 [auto_handle – členové](../dotnet/auto-handle-members.md)   
 [auto_handle::operator!](../dotnet/auto-handle-operator-logical-not.md)
---
title: auto_handle::Release | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- msclr::auto_handle::release
- auto_handle.release
- msclr.auto_handle.release
- auto_handle::release
dev_langs: C++
helpviewer_keywords: auto_handle::release
ms.assetid: d4848150-859e-4c61-a946-09d24d3d6577
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f010429904df409b1514dc811d160182f2291227
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="autohandlerelease"></a>auto_handle::release
Uvolní objekt z `auto_handle` správy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
_element_type ^ release();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Vydaná objekt.  
  
## <a name="example"></a>Příklad  
  
```  
// msl_auto_handle_release.cpp  
// compile with: /clr  
#include <msclr\auto_handle.h>  
  
using namespace System;  
using namespace msclr;  
  
ref class ClassA {  
   String^ m_s;  
public:  
   ClassA( String^ s ) : m_s( s ) {  
      Console::WriteLine( "ClassA constructor: " + m_s );  
   }  
   ~ClassA() {  
      Console::WriteLine( "ClassA destructor: " + m_s );  
   }  
  
   void PrintHello() {  
      Console::WriteLine( "Hello from {0} A!", m_s );     
   }  
};  
  
int main()  
{  
   ClassA^ a;  
  
   // create a new scope:  
   {  
      auto_handle<ClassA> agc1 = gcnew ClassA( "first" );  
      auto_handle<ClassA> agc2 = gcnew ClassA( "second" );  
      a = agc1.release();  
   }  
   // agc1 and agc2 go out of scope here  
  
   a->PrintHello();  
  
   Console::WriteLine( "done" );  
}  
```  
  
```Output  
ClassA constructor: first  
ClassA constructor: second  
ClassA destructor: second  
Hello from first A!  
done  
```  
  
## <a name="requirements"></a>Požadavky  
 **Soubor hlaviček** \<msclr\auto_handle.h >  
  
 **Namespace** msclr –  
  
## <a name="see-also"></a>Viz také  
 [auto_handle – členové](../dotnet/auto-handle-members.md)   
 [auto_handle –:: ~ auto_handle –](../dotnet/auto-handle-tilde-auto-handle.md)   
 [auto_handle::Reset](../dotnet/auto-handle-reset.md)
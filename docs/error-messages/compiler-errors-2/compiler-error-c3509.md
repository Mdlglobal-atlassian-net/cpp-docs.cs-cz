---
title: "C3509 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3509
dev_langs: C++
helpviewer_keywords: C3509
ms.assetid: cc2db39a-2f98-4e40-b803-496e585494e6
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bb8fcb4c51ce0a7e69154e77ac5990898275ba16
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3509"></a>C3509 chyby kompilátoru
'type': neplatný návratový typ automatizace; Když parametr je označen jako 'retval', návratový typ musí být 'zrušit', 'HRESULT' nebo 'kód SCODE.  
  
 Metoda v rozhraní modelu COM musí vracet buď void nebo HRESULT.  
  
 Následující ukázka generuje C3509:  
  
```  
// C3509.cpp  
#define _ATL_DEBUG_QI  
  
#define WIN32_LEAN_AND_MEAN   // Exclude rarely-used stuff from Windows headers  
#define STRICT  
#ifndef _WIN32_WINNT  
#define _WIN32_WINNT 0x0400  
#endif  
  
#define _ATL_ATTRIBUTES 1  
#include <atlbase.h>  
extern CComModule _Module;  
#include <atlcom.h>  
#include <atlctl.h>  
#include <atlstr.h>  
  
[module(name=oso)];  
  
[dispinterface, uuid(00000000-0000-0000-0000-000000000001)]  
__interface I {  
   [id(1)] int f([out, retval] int*);   // C3509  
   // try the following line instead  
   // [id(1)] void f([out, retval] int*);  
};  
  
[coclass, uuid(00000000-0000-0000-0000-000000000002)]  
struct C : I {  
   int f(int*) {  
   // try the following line instead, and delete return statement  
   // void f(int*) {  
      return 0;  
   }  
};  
  
int main() {  
}  
```
---
title: C3340 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3340
dev_langs:
- C++
helpviewer_keywords:
- C3340
ms.assetid: 23b12298-b92a-4717-8380-f165c998cb8a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc5c412f34c12bcfe890e71cdbe59bd6f8ee7a63
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33255120"
---
# <a name="compiler-error-c3340"></a>C3340 chyby kompilátoru
"rozhraní": rozhraní nemůže být "s omezeným přístupem" a "default" v třída typu coclass 'class'.  
  
 [s omezeným přístupem](../../windows/restricted.md) atribut a [výchozí](../../windows/default-cpp.md) atribut se vzájemně vylučují.  
  
 Následující ukázka generuje C3340:  
  
```  
// C3340.cpp  
#include <windows.h>  
[module(name="MyModule")];  
  
[ object, uuid(373a1a4c-469b-11d3-a6b0-00c04f79ae8f) ]  
__interface IMyIface  
{  
   HRESULT f1();  
};  
  
[ coclass, uuid(373a1a4d-469b-11d3-a6b0-00c04f79ae8f),  
default(IMyIface),  
source(IMyIface),restricted(IMyIface) ]  
class CmyClass // C3340  
{  
};  
  
int main()  
{  
}  
```
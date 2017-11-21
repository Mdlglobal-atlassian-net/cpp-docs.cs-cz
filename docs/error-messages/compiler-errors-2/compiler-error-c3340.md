---
title: "C3340 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3340
dev_langs: C++
helpviewer_keywords: C3340
ms.assetid: 23b12298-b92a-4717-8380-f165c998cb8a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: fafe0e3131512aff530f88daf023d76a47b7d3ab
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
---
title: "Kompilátoru (úroveň 4) upozornění C4682 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4682
dev_langs: C++
helpviewer_keywords: C4682
ms.assetid: 858ea157-1244-4a61-85df-97b3de43d418
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 95409a9c23b9f0cc7a034323e661ce1ce0e4b173
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4682"></a>C4682 kompilátoru upozornění (úroveň 4)
"parametr": atribut směrovou parametr zadán, jako výchozí bude použit [v]  
  
 Metoda na parametr v rozhraní s atributy nemá jeden z atributů směrovou: [v](../../windows/in-cpp.md) nebo [out](../../windows/out-cpp.md). Parametr výchozí v.  
  
 Toto upozornění je ve výchozím nastavení vypnutý. V tématu [kompilátoru upozornění, že jsou vypnout ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.  
  
 Následující ukázka generuje C4682:  
  
```  
// C4682.cpp  
// compile with: /W4  
#pragma warning(default : 4682)  
#include <windows.h>  
[module(name="MyModule")];  
  
[ library_block, object, uuid("c54ad59d-d516-41dd-9acd-afda17565c2b") ]  
__interface IMyIface : IUnknown  
{  
   HRESULT f1(int i, int *pi); // C4682  
   // try the following line  
   // HRESULT f1([in] int i, [in] int *pi);  
};  
  
int main()  
{  
}  
```
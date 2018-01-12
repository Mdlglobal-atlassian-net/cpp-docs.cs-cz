---
title: "C2435 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2435
dev_langs: C++
helpviewer_keywords: C2435
ms.assetid: be6aa8f8-579b-42ea-bdd8-2d01393646ad
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1616208a5ea0b8c3680e87a23846fc58be816623
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2435"></a>C2435 chyby kompilátoru
'příkaz var': dynamické inicializace vyžaduje spravované CRT, nelze kompilovat s/clr: safe  
  
 **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015.  
  
 Inicializace proměnné globální pro aplikační doménu vyžaduje CRT kompilovat s `/clr:pure`, který nevytváří ověřitelný bitové kopie.  
  
 Další informace najdete v tématu [appdomain](../../cpp/appdomain.md) a [proces](../../cpp/process.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2435:  
  
```  
// C2435.cpp  
// compile with: /clr:safe /c  
int globalvar = 0;   // C2435  
  
__declspec(process)  
int globalvar2 = 0;  
```
---
title: "Kompilátoru (úroveň 1) upozornění C4083 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4083
dev_langs: C++
helpviewer_keywords: C4083
ms.assetid: e7d3344e-5645-4d56-8460-d1acc9145ada
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 66a614d71e27b6a90500bd6e3b24f6894a9d5820
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4083"></a>C4083 kompilátoru upozornění (úroveň 1)
očekávaný token; najít identifikátor "identifikátor"  
  
 Identifikátor dojde k nesprávné místo v **#pragma** příkaz.  
  
## <a name="example"></a>Příklad  
  
```  
// C4083.cpp  
// compile with: /W1 /LD  
#pragma warning disable:4083    // C4083  
#pragma warning(disable:4083)   //correct  
```  
  
 Zkontrolujte syntaxi [#pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md) direktivy.
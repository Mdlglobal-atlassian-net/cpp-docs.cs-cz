---
title: "C3126 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3126
dev_langs: C++
helpviewer_keywords: C3126
ms.assetid: e72658a3-5d85-4a31-89a4-dbc3d475973d
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5b12b0ec06d45c68427856ab226e2ea09fc05920
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3126"></a>C3126 chyby kompilátoru
nelze definovat union, union' uvnitř spravovaného typu "typ"  
  
 Sjednocení nemůže být definovaný uvnitř spravovaného typu.  
  
 Následující ukázka generuje C3126:  
  
```  
// C3126_2.cpp  
// compile with: /clr /c  
ref class Test  
{  
   union x  
   {   // C3126  
      int a;  
      int b;  
   };  
};  
```  
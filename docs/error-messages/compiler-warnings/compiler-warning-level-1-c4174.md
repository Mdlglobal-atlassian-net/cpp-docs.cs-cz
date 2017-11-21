---
title: "Kompilátoru (úroveň 1) upozornění C4174 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4174
dev_langs: C++
helpviewer_keywords: C4174
ms.assetid: 63301e51-24bc-43c4-bb11-252f7d513e9e
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d844ac3b2cf5660053289aa0aa0af99549553876
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4174"></a>C4174 kompilátoru upozornění (úroveň 1)
"název": není k dispozici jako součást #pragma  
  
## <a name="example"></a>Příklad  
  
```  
// C4174.cpp  
// compile with: /W1  
#pragma component(info)  // C4174; unknown  
#pragma component(browser, off)  // turn off browse info  
int main()  
{  
}  
```
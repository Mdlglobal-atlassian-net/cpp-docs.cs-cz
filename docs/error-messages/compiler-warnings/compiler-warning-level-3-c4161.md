---
title: "Kompilátoru (úroveň 3) upozornění C4161 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4161
dev_langs: C++
helpviewer_keywords: C4161
ms.assetid: 03d3be61-83f1-4009-8310-8758ab67055f
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1d61de9a9a02f55114319af677db29630038966a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4161"></a>C4161 kompilátoru upozornění (úroveň 3)
\#Direktiva pragma pragma(pop...): více bodů POP než nabízených oznámení  
  
 Protože jeden zdrojový kód obsahuje více pop než nabízených oznámení pro – Direktiva pragma ***– Direktiva pragma***, nemusí se zásobníkem chovat podle očekávání. Abyste se vyhnuli upozornění, ujistěte se, že počet bodů POP není delší než počet nabízených oznámení.  
  
## <a name="example"></a>Příklad  
 Následující příklad generuje C4161:  
  
```  
// C4161.cpp  
// compile with: /W3 /LD  
#pragma pack(push, id)  
#pragma pack(pop, id)  
#pragma pack(pop, id)   // C4161, an extra pop  
  
#pragma bss_seg(".my_data1")  
int j;  
  
#pragma bss_seg(push, stack1, ".my_data2")     
int l;  
  
#pragma bss_seg(pop, stack1)  
int m;  
  
#pragma bss_seg(pop, stack1)   // C4161  
```
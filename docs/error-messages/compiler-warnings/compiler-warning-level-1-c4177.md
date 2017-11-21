---
title: "Kompilátoru (úroveň 1) upozornění C4177 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4177
dev_langs: C++
helpviewer_keywords: C4177
ms.assetid: 2b05a5b3-696e-4f21-818e-227b9335e748
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d4555be65a02011d3e3e429f1f172f88f5f50614
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4177"></a>C4177 kompilátoru upozornění (úroveň 1)
\#pragma – Direktiva pragma by měla být v globálním oboru  
  
 [– Direktiva pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md) – Direktiva pragma by se neměla používat v rámci místního oboru. **– Direktiva pragma** nebude platný až do globální obor po aktuálním oboru.  
  
 Následující ukázka generuje C4177:  
  
```  
// C4177.cpp  
// compile with: /W1  
// #pragma bss_seg("global")   // OK  
  
int main() {  
   #pragma bss_seg("local")    // C4177  
}  
```
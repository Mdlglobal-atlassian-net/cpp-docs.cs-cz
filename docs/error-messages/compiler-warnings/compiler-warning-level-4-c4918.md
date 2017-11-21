---
title: "Kompilátoru (úroveň 4) upozornění C4918 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4918
dev_langs: C++
helpviewer_keywords: C4918
ms.assetid: 1bcf6d35-3467-4aa8-b2ef-cb33f4e70238
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7c00b7bfe6c7464dfbf49480a533de465ae2e58f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4918"></a>C4918 kompilátoru upozornění (úroveň 4)
'znak': neplatný znak v seznamu optimalizace – Direktiva pragma  
  
 V seznamu optimalizace byl nalezen neznámý znak [optimalizovat](../../preprocessor/optimize.md) – Direktiva pragma příkaz.  
  
 Například následující příkaz generuje C4918:  
  
```  
// C4918.cpp  
// compile with: /W4  
#pragma optimize("X", on) // C4918 expected  
int main()  
{  
}  
```
---
title: "C3417 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3417
dev_langs: C++
helpviewer_keywords: C3417
ms.assetid: 3e7869ea-8948-42fb-ba30-6ccafe499c35
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e25adc1b699998235c1cfa16edbb50c2b774f983
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3417"></a>C3417 chyby kompilátoru
"člen": hodnota typy nemohou obsahovat uživatelem definované speciální členské funkce  
  
 Typy hodnot nemůže obsahovat funkce jako je například výchozí konstruktor instance, destruktor nebo kopírovacího konstruktoru.  
  
 Následující ukázka generuje C3517:  
  
```  
// C3417.cpp  
// compile with: /clr /c  
value class VC {  
   VC(){}   // C3417  
  
   // OK  
   static VC(){}  
   VC(int i){}  
};  
```
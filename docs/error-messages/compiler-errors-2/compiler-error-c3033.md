---
title: "C3033 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3033
dev_langs: C++
helpviewer_keywords: C3033
ms.assetid: 8628b6bb-a650-4ed2-af13-57acd2f7ddbb
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c005874c7a11f5ec250daa42f8857070bbfad8dc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3033"></a>C3033 chyby kompilátoru
'příkaz var': proměnné v klauzuli ' klauzule nemůže mít typ kvalifikovaný const  
  
 Hodnoty předaný určité klauzule nelze `const` proměnné.  
  
 Následující ukázka generuje C3033:  
  
```  
// C3033.cpp  
// compile with: /openmp /link vcomps.lib  
int main() {  
   const int val = 1;  
   int val2 = 1;  
  
   #pragma omp parallel reduction(+ : val)   // C3033  
   ;  
  
   #pragma omp parallel reduction(+ : val2)   // OK  
   ;  
}  
```
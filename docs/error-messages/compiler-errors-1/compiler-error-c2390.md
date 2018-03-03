---
title: "C2390 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2390
dev_langs:
- C++
helpviewer_keywords:
- C2390
ms.assetid: 06b749ee-d072-4db1-b229-715f2c0728b5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 93d4cbd9de274d53fdc0369c2b85dbf2e97af48f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2390"></a>C2390 chyby kompilátoru
"identifikátor": Třída nesprávné úložiště 'specifikátor.  
  
 Třídy úložiště není platný pro identifikátor globální obor. Místo neplatná třída se používá výchozí třídu úložiště.  
  
 Možná řešení:  
  
-   Pokud je identifikátor funkci, deklarujte ji s `extern` úložiště.  
  
-   Pokud je identifikátor formální parametr nebo místní proměnné, deklarujte ji s úložištěm automaticky.  
  
-   Pokud je identifikátor globální proměnné, deklarujte ji s neexistuje žádná třída úložiště (automatické úložiště).  
  
## <a name="example"></a>Příklad  
  
-   Následující ukázka generuje C2390:  
  
```  
// C2390.cpp  
register int i;   // C2390  
  
int main() {  
   register int j;   // OK  
}  
```
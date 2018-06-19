---
title: C2390 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2390
dev_langs:
- C++
helpviewer_keywords:
- C2390
ms.assetid: 06b749ee-d072-4db1-b229-715f2c0728b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5a32a9ca77ba43e5f2866baed91b99103224dbc0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33198713"
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
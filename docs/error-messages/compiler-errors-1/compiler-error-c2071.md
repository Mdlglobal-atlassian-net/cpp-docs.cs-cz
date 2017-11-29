---
title: "C2071 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2071
dev_langs: C++
helpviewer_keywords: C2071
ms.assetid: f8c09255-a5c4-47e3-8089-3d875ae43cc5
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c62bb735a84b04bfb0c1addd5e3dd20a48a3eb33
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2071"></a>C2071 chyby kompilátoru
"identifikátor": Neplatný úložiště – třída  
  
 `identifier`byla deklarována s neplatnou [třídy úložiště](../../c-language/c-storage-classes.md). Tato chyba může být způsobena Pokud pro identifikátor je zadána více než jednu třídu úložiště nebo pokud definice není kompatibilní s deklaraci třídy úložiště.  
  
 Chcete-li tento problém vyřešit, pochopit třídy určený úložiště identifikátoru – například `static` nebo `extern`– a opravte deklaraci tak, aby odpovídaly.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2071.  
  
```  
// C2071.cpp  
// compile with: /c  
struct C {  
   extern int i;   // C2071  
};  
struct D {  
   int i;   // OK, no extern on an automatic  
};  
```  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2071.  
  
```  
// C2071_b.cpp  
// compile with: /c  
typedef int x(int i) { return i; }   // C2071  
typedef int (x)(int);   // OK, no local definition in typedef  
```
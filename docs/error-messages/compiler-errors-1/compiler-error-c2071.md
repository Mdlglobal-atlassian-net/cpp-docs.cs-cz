---
title: C2071 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2071
dev_langs:
- C++
helpviewer_keywords:
- C2071
ms.assetid: f8c09255-a5c4-47e3-8089-3d875ae43cc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: faee56023d14e9b010d1c691af654ffcbc31dc78
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33169202"
---
# <a name="compiler-error-c2071"></a>C2071 chyby kompilátoru
"identifikátor": Neplatný úložiště – třída  
  
 `identifier` byla deklarována s neplatnou [třídy úložiště](../../c-language/c-storage-classes.md). Tato chyba může být způsobena Pokud pro identifikátor je zadána více než jednu třídu úložiště nebo pokud definice není kompatibilní s deklaraci třídy úložiště.  
  
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
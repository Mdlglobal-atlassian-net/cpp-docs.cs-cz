---
title: Kompilátoru (úroveň 1) upozornění C4632 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4632
dev_langs:
- C++
helpviewer_keywords:
- C4632
ms.assetid: 9e35d205-cf21-4e34-8bd5-e1e7b0e2cdd3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4aa05b039d3d4a8cddcc607861ea27e9591cfc29
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33278562"
---
# <a name="compiler-warning-level-1-c4632"></a>C4632 kompilátoru upozornění (úroveň 1)
Komentář dokumentu XML: soubor – přístup byl odepřen: důvod  
  
 Cesta k souboru projektový (`file`) nebyla platná a žádné projektový soubor.  
  
 Následující ukázka generuje C4632:  
  
```  
// C4632.cpp  
// compile with: /clr /docv:\\falsedir /LD /W1  
// C4632 expected  
  
/// Text for class MyClass.  
public ref class MyClass {};  
```
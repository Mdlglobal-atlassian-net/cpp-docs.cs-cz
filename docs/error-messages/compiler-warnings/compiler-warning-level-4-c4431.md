---
title: Kompilátoru (úroveň 4) upozornění C4431 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4431
dev_langs:
- C++
helpviewer_keywords:
- C4431
ms.assetid: 58434ab6-dd8d-427b-953a-602fb7453ae6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2bb5a76a1ddf1f1104fe88511c9bf9bf88bf6602
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292253"
---
# <a name="compiler-warning-level-4-c4431"></a>C4431 kompilátoru upozornění (úroveň 4)
chybějící specifikátor typu: předpokládá se int Poznámka: C již nepodporuje výchozí int.  
  
 Tato chyba může vygenerovaného jako výsledek kompilátoru shoda práci, kterou bylo provedeno pro Visual C++ 2005: Visual C++ už vytvoří netypové identifikátory jako int ve výchozím nastavení. Je třeba explicitně zadat typ identifikátoru.  
  
 Toto upozornění je ve výchozím nastavení vypnutý. V tématu [kompilátoru upozornění, že jsou vypnout ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4431.  
  
```  
// C4431.c  
// compile with: /c /W4  
#pragma warning(default:4431)  
i;   // C4431  
int i;   // OK  
```
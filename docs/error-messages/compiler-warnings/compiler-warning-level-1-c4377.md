---
title: Kompilátoru (úroveň 1) upozornění C4377 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4377
dev_langs:
- C++
helpviewer_keywords:
- C4377
ms.assetid: a1c797b8-cd5e-4a56-b430-d07932e811cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef049f85cd17bfeaba243b84da9fca93ae4036b0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33274778"
---
# <a name="compiler-warning-level-1-c4377"></a>C4377 kompilátoru upozornění (úroveň 1)
nativní typy jsou privátní ve výchozím nastavení; -d1PrivateNativeTypes je zastaralý.  
  
 V předchozích verzích byly nativní typy v sestavení veřejné ve výchozím nastavení a – možnost kompilátoru interní, nedokumentovanými (**/d1PrivateNativeTypes**) byla použita k nastavit jako soukromé.  
  
 Všechny typy nativní a CLR, jsou nyní soukromé ve výchozím nastavení v sestavení, takže **/d1PrivateNativeTypes** již není potřeba.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4377.  
  
```  
// C4377.cpp  
// compile with: /clr /d1PrivateNativeTypes /W1  
// C4377 warning expected  
int main() {}  
```
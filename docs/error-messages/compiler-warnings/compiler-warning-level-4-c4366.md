---
title: "Kompilátoru (úroveň 4) upozornění C4366 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4366
dev_langs: C++
helpviewer_keywords: C4366
ms.assetid: 65d2942f-3741-42f4-adf2-4920d5a055ca
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 221cc02e5a2592599bad0ee9a77de59b19dda6f5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4366"></a>C4366 kompilátoru upozornění (úroveň 4)
Výsledek unární operátor 'operátor' může nezarovnané  
  
 Pokud členem struktura může být někdy nezarovnané kvůli okolních, kompilátor upozornění, když, je přiřazena adresa člena zarovnaný ukazatele. Ve výchozím nastavení je zarovnán všechny odkazy.  
  
 C4366 vyřešit, změňte zarovnání struktury nebo deklarovat ukazatel pomocí [__unaligned](../../cpp/unaligned.md) – klíčové slovo.  
  
 Další informace najdete v tématu __unaligned a [pack](../../preprocessor/pack.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4366.  
  
```  
// C4366.cpp  
// compile with: /W4 /c  
// processor: IPF x64  
#pragma pack(1)  
struct X {  
   short s1;  
   int s2;  
};  
  
int main() {  
   X x;  
   short * ps1 = &x.s1;   // OK  
   int * ps2 = &x.s2;   // C4366  
}  
```
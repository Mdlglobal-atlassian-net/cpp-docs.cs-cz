---
title: "Kompilátoru (úroveň 4) upozornění C4295 | Microsoft Docs"
ms.custom: 
ms.date: 1/09/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4295
dev_langs: C++
helpviewer_keywords: C4295
ms.assetid: 20dbff85-9f62-4ca3-8fe9-079d4512006d
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 56ffdce8c2790a3944a8f79753177bc80e249778
ms.sourcegitcommit: bc086a7acbe2d9fd77d115f269cc2a0dbeeb5b88
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2018
---
# <a name="compiler-warning-level-4-c4295"></a>C4295 kompilátoru upozornění (úroveň 4)
  
> '*pole*': pole je příliš malá, aby zahrnují ukončující znak hodnoty null  
  
Byl inicializován pole, ale jeho poslední znak v poli není null; přístup k poli jako řetězec může vést k neočekávaným výsledkům.  
  
## <a name="example"></a>Příklad  
  
Následující ukázka generuje C4295. Chcete-li tento problém vyřešit, je může deklarovat velikosti pole větší pro uložení ukončující hodnotu null z inicializátoru řetězec, nebo můžete použít pole inicializátoru seznamu aby záměrné zaškrtnutí, že toto je pole `char`, není řetězce ukončené hodnotou null.  
  
```C  
// C4295.c
// compile with: /W4


int main() {
   char a[3] = "abc";           // C4295
   char b[3] = {'d', 'e', 'f'}; // No warning
   a[0] = b[2];
}
```

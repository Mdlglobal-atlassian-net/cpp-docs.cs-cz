---
title: Kompilátoru (úroveň 4) upozornění C4295 | Microsoft Docs
ms.custom: ''
ms.date: 1/09/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4295
dev_langs:
- C++
helpviewer_keywords:
- C4295
ms.assetid: 20dbff85-9f62-4ca3-8fe9-079d4512006d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 815a669bc359121b13b1d636009cad81dc332304
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33296299"
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

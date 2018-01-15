---
title: "Kompilátoru (úroveň 4) upozornění C4463 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4463
dev_langs: C++
helpviewer_keywords: C4463
ms.assetid: a07ae70c-db4e-472b-8b58-9137d9997323
caps.latest.revision: "0"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 71b438de515a4fd01e7714de685ee0a89adb609e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4463"></a>C4463 kompilátoru upozornění (úroveň 4)  
  
> přetečení; přiřazení *hodnotu* bitová pole, které může obsahovat pouze hodnoty z *low_value* k *high_value*  
  
Přiřazená *hodnota* je mimo rozsah hodnoty, které mohou být uloženy pole verze. Typy signed bitové pole použijte nejvyšších bit pro přihlášení, takže když  *n*  se velikost pole bit rozsahu podepsaný bitová pole-2<sup>n-1</sup> 2<sup>n-1</sup>-1, zatímco nepodepsané bitová pole mají rozsahu od 0 do 2<sup>n</sup>-1.  
  
## <a name="example"></a>Příklad  
  
Tento příklad vytvoří C4463, protože se pokouší přiřadit hodnotu 3 bitová pole typu `int` s velikostí 2, který má rozmezí -2 a 1.  
  
Chcete-li tento problém vyřešit, můžete změnit přiřazené hodnoty na něco v povoleném rozsahu. Pokud pole bit slouží k uložení nepodepsané hodnoty v rozsahu od 0 do 3, můžete změnit typ deklarace k `unsigned`. Pokud toto pole je určena pro uložení hodnoty v rozsahu -4 až 3, můžete změnit velikost pole bit do 3.  
  
```cpp  
// C4463_overflow.cpp
// compile with: cl /W4 /EHsc C4463_overflow.cpp
struct S { 
    int x : 2; // int type treats high-order bit as sign
}; 

int main() { 
    S s; 
    s.x = 3; // warning C4463: overflow; assigning 3 
    // to bit-field that can only hold values from -2 to 1 
    // To fix, change assigned value to fit in range,
    // increase size of bitfield, and/or change base type 
    // to unsigned.
} 
```  

---
title: Kompilátoru (úroveň 1) upozornění C4369 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4369
dev_langs:
- C++
helpviewer_keywords:
- C4369
ms.assetid: ade87e84-36be-4e00-be99-2930af848feb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 63445f0713b43ce7fde418ebd9d65403965c07ba
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4369"></a>C4369 kompilátoru upozornění (úroveň 1)
'enumerátor': hodnotu výčtu 'Hodnota' nemůže být reprezentován jako "typ", hodnota je 'nová_hodnota.  
  
 Enumerátor výpočtu být větší než největší hodnota zadaného základního typu.  To způsobilo přetečení a kompilátor zabalená hodnota výčtu, která má nejnižší možná hodnota pro typ.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4369.  
  
```  
// C4369.cpp  
// compile with: /W1  
int main() {  
   enum Color: char { red = 0x7e, green, blue };   // C4369  
   enum Color2: char { red2 = 0x7d, green2, blue2};   // OK  
}  
```
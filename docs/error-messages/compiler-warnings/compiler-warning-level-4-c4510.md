---
title: Kompilátoru (úroveň 4) upozornění C4510 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4510
dev_langs:
- C++
helpviewer_keywords:
- C4510
ms.assetid: fd28d1d4-ad27-4dad-94c0-9dba46c93180
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5b280a15381f53b6836b321e25717cbed19c7271
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4510"></a>C4510 kompilátoru upozornění (úroveň 4)
'class': Nepodařilo se vygenerovat výchozí konstruktor  
  
 Kompilátor nemůže generovat výchozí konstruktor pro zadanou třídu a byl vytvořen žádný konstruktor definovaný uživatelem. Nebudete moci vytvořit objekty tohoto typu.  
  
 Existuje několik situací, které brání kompilátor generování výchozí konstruktor, včetně:  
  
-   Const datový člen.  
  
-   Data člena, který je odkaz.  
  
 Budete muset vytvořit uživateli definované výchozí konstruktor pro třídu, která inicializuje tito členové.  
  
 Následující ukázka generuje C4510:  
  
```  
// C4510.cpp  
// compile with: /W4  
struct A {  
   const int i;  
   int &j;  
   A& operator=( const A& ); // C4510 expected  
   // uncomment the following line to resolve this C4510  
   // A(int ii, int &jj) : i(ii), j(jj) {}  
};   // C4510  
  
int main() {  
}  
```
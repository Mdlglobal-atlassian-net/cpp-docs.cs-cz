---
title: "Kompilátoru (úroveň 4) upozornění C4510 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4510
dev_langs: C++
helpviewer_keywords: C4510
ms.assetid: fd28d1d4-ad27-4dad-94c0-9dba46c93180
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 372dd9c789c54a38a5eed2c5f457c518989ede17
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
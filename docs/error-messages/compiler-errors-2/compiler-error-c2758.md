---
title: "C2758 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2758
dev_langs: C++
helpviewer_keywords: C2758
ms.assetid: 1d273034-194c-4926-9869-142d1b219cbe
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f694df9f39edbc257b887bcfd9bd13a0ba31a1a0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2758"></a>C2758 chyby kompilátoru
"člen": členem typ odkazu musí být inicializován.  
  
 Chyba kompilátoru C2758 dojde, pokud nebude členem odkaz v seznamu inicializátoru konstruktoru se inicializovat. Kompilátor zanechává člen není definovaná. Odkazovat člen, proměnné musí inicializovat při deklarován nebo mít hodnotu v seznamu inicializace konstruktoru.  
  
 Následující ukázka generuje C2758:  
  
```  
// C2758.cpp  
// Compile by using: cl /W3 /c C2758.cpp  
struct A {  
   const int i;  
  
   A(int n) { };   // C2758  
   // try the following line instead  
   // A(int n) : i{n} {};  
};  
```
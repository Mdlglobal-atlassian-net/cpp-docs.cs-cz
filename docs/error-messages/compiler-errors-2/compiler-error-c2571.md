---
title: "C2571 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2571
dev_langs: C++
helpviewer_keywords: C2571
ms.assetid: c6522616-dee9-4d7d-9bf8-30a7e1deaadf
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8bfb4f9af849efea2fa3aa8a84a57f1cfb4cd502
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2571"></a>C2571 chyby kompilátoru
'function': virtuální funkce nelze v union, union.  
  
 Spojení je deklarovaný s virtuální funkce. Virtuální funkce pouze ve třídě nebo struktuře můžou deklarovat.  Možná řešení:  
  
1.  Změňte sjednocení na třídu nebo strukturu.  
  
2.  Ujistěte se, funkce nevirtuální.  
  
 Následující ukázka generuje C2571:  
  
```  
// C2571.cpp  
// compile with: /c  
union A {  
   virtual void func1();   // C2571  
   void func2();   // OK  
};  
```
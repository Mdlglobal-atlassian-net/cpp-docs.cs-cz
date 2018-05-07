---
title: Kompilátoru (úroveň 1) upozornění C4526 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4526
dev_langs:
- C++
helpviewer_keywords:
- C4526
ms.assetid: 490f8916-5fdc-4cad-b412-76c3382a5976
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5a38d629d61e16b038701522d4bb27a4de7391d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4526"></a>C4526 kompilátoru upozornění (úroveň 1)
'function': statické členské funkce nelze přepsat virtuální funkce ' virtuální function'override ignorovány, bude skrytá virtuální funkce  
  
 Funkce statický člen splňuje kritéria pro přepsání virtuální funkce, který virtuální a statické členské funkce.  
  
 Následující kód generuje C4526:  
  
```  
// C4526.cpp  
// compile with: /W1 /c  
// C4526 expected  
struct myStruct1 {  
   virtual void __stdcall func( int ) = 0;  
};  
  
struct myStruct2: public myStruct1 {  
   static void __stdcall func( int );  
};  
```  
  
 Toto jsou možné opravy:  
  
-   Pokud funkce byla určena k přepsání virtuální funkce základní třídy, odeberte statický specifikátor.  
  
-   Pokud funkci neměla být statické členské funkce, přejmenujte ji, není v konfliktu s virtuální funkce základní třídy.
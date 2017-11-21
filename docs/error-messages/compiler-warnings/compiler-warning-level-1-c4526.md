---
title: "Kompilátoru (úroveň 1) upozornění C4526 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4526
dev_langs: C++
helpviewer_keywords: C4526
ms.assetid: 490f8916-5fdc-4cad-b412-76c3382a5976
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 00ffa9e20781d8d5d1405d6bf5546b47a6530b88
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
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
ms.workload: cplusplus
ms.openlocfilehash: a74d7d2e2c745a4c8e29736c1e3a7fc38892d5f6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
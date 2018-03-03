---
title: "C2555 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2555
dev_langs:
- C++
helpviewer_keywords:
- C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c66b464ac38a46716fbed972939feef1273ad03d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2555"></a>C2555 chyby kompilátoru
'class1::function1': přepisování virtuální funkce návratový typ se liší a není kovariantní z 'class2::function2.  
  
 Virtuální funkce a odvozené přepsání funkce mají seznamy identické parametrů ale jiné návratové typy. Funkce přepsání v odvozené třídě nemůže lišit od virtuální v základní třídě pouze podle její návratový typ funkce.  
  
 Chcete-li tuto chybu vyřešit, přetypovat návratovou hodnotu po virtuální funkce byla volána.  
  
 Tato chyba se může zobrazit také v případě kompilace s volbou/CLR.   Například Visual C++ ekvivalentní následující deklaraci C#:  
  
```  
Guid[] CheckSources(Guid sourceID, Guid[] carouselIDs);  
```  
  
 is  
  
```  
Guid CheckSources(Guid sourceID, Guid carouselIDs[]) [];  
```  
  
 Další informace o C2555 najdete v článku znalostní báze Knowledge Base Q240862.  
  
 Následující ukázka generuje C2555:  
  
```  
// C2555.cpp  
// compile with: /c  
struct X {  
   virtual void func();  
};  
struct Y : X {  
   char func();  // C2555  
   void func2();   // OK  
};  
```
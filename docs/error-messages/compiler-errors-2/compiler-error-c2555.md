---
title: C2555 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2555
dev_langs:
- C++
helpviewer_keywords:
- C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d2d1a710177e2c8c72b0afeff662dddf1c22ef5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33230581"
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
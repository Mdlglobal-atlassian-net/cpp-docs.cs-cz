---
title: "C2695 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2695
dev_langs: C++
helpviewer_keywords: C2695
ms.assetid: 3f6f2091-c38b-40ea-ab6c-f1846f5702d7
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1ae253ade1093d447616a39e788a80b843290f6a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2695"></a>C2695 chyby kompilátoru
'function1': přepisování virtuální funkce se liší od "funkce2" pouze podle konvence volání  
  
 Podpis funkce v odvozené třídě nelze přepsat funkce v základní třídě a změnit konvence volání.  
  
 Následující ukázka generuje C2695:  
  
```  
// C2695.cpp  
class C {  
   virtual void __fastcall func();  
};  
  
class D : public C {  
   virtual void __clrcall func();   // C2695  
};  
```
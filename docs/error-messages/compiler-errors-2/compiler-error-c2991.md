---
title: "C2991 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2991
dev_langs: C++
helpviewer_keywords: C2991
ms.assetid: a87e4404-26e8-4927-b3ee-5d02b3b8bee1
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 44854e546449fe03457b7adc310abc36d1ce51f7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2991"></a>C2991 chyby kompilátoru
Předefinování parametr typu "parametr"  
  
 Došlo ke konfliktu typ mezi dvěma obecného nebo šablony definice `parameter`. Při definování několik parametrů obecného nebo šablonu, musí používat ekvivalentní typy.  
  
 Následující ukázka generuje C2991:  
  
```  
// C2991.cpp  
// compile with: /c  
template<class T, class T> struct TC {};   // C2991  
// try the following line instead  
// template<class T, class T2> struct TC {};  
```  
  
 C2991 může dojít také při použití obecných typů:  
  
```  
// C2991b.cpp  
// compile with: /clr /c  
generic<class T,class T> ref struct GC {};   // C2991  
// try the following line instead  
// generic<class T,class T2> ref struct GC {};  
```
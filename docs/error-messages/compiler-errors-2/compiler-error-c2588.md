---
title: "C2588 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2588
dev_langs: C++
helpviewer_keywords: C2588
ms.assetid: 19a0cabd-ca13-44a5-9be3-ee676abf9bc4
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c6d71e5bfe442f2b3f2225cd4dc6cb88fc73d24a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2588"></a>C2588 chyby kompilátoru
':: ~ identifikátor ': Neplatný globální – destruktor  
  
 Destruktoru je určená pro něco jiného než třídy, struktury nebo sjednocení. Toto není povoleno.  
  
 Tato chyba může být způsobeno chybějící třída, struktura nebo union název na levé straně řešení rozsahu (`::`) operátor.  
  
 Následující ukázka generuje C2588:  
  
```  
// C2588.cpp  
~F();   // C2588  
```
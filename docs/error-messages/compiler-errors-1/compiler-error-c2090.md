---
title: "C2090 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2090
dev_langs: C++
helpviewer_keywords: C2090
ms.assetid: e8176e55-382b-453d-aa27-6597f0274afd
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9a60a4e2d1a5db0a698e210ca5ed1360a96ffdc6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2090"></a>C2090 chyby kompilátoru
Funkce vrátí pole  
  
 Funkce nemohou vrátit pole. Místo toho vrátí ukazatel na pole.  
  
 Následující ukázka generuje C2090:  
  
```  
// C2090.cpp  
int func1(void)[] {}   // C2090  
```  
  
 Možná řešení:  
  
```  
// C2090b.cpp  
// compile with: /c  
int* func2(int * i) {  
   return i;  
}  
```
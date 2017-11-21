---
title: "C2033 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2033
dev_langs: C++
helpviewer_keywords: C2033
ms.assetid: fd5a1637-9db2-4c98-a7cc-b63b39737cd9
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ba0fcc5d0938c796c94e6201be18d6c1fb6158b0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2033"></a>C2033 chyby kompilátoru
"identifikátor": bit pole nemůže mít indirection  
  
 Bitová pole byla deklarována jako ukazatel, což není povoleno.  
  
 Následující ukázka generuje C2033:  
  
```  
// C2033.cpp  
struct S {  
   int *b : 1;  // C2033  
};  
```  
  
 Možná řešení:  
  
```  
// C2033b.cpp  
// compile with: /c  
struct S {  
   int b : 1;  
};  
```
---
title: "C2208 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2208
dev_langs: C++
helpviewer_keywords: C2208
ms.assetid: 9ae704bc-bf70-45f1-8e47-0470f21edd4e
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1fd07ee02251a3ea1ef7b0da1bc8e27685eb42ff
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2208"></a>C2208 chyby kompilátoru
'type': žádní členové definovat pomocí tohoto typu  
  
 Identifikátor překladu názvu typu je v agregační deklaraci, ale kompilátor nelze deklarovat členem.  
  
 Následující ukázka generuje C2208:  
  
```  
// C2208.cpp  
class C {  
   C;   // C2208  
   C(){}   // OK  
};  
```
---
title: "Kompilátoru (úroveň 1) upozornění C4804 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4804
dev_langs: C++
helpviewer_keywords: C4804
ms.assetid: 069e8f44-3ef6-43bb-8524-4116fc6eea83
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 95a96844406bb803c46bd4f1b0162be711105394
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4804"></a>C4804 kompilátoru upozornění (úroveň 1)
'operace': unsafe použití typu, bool, v operaci  
  
 Toto upozornění je pro, když jste použili `bool` proměnné nebo hodnota neočekávaným způsobem. Například C4804 se vygeneruje, pokud používáte operátorů, například záporné unárního operátoru (**-**) nebo doplňkovým operátorem (`~`). Kompilátor vyhodnotí výraz.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4804:  
  
```  
// C4804.cpp  
// compile with: /W1  
  
int main()  
{  
   bool i = true;  
   if (-i)   // C4804, remove the '-' to resolve  
   {  
      i = false;  
   }  
}  
```
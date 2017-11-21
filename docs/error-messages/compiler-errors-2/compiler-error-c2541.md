---
title: "C2541 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2541
dev_langs: C++
helpviewer_keywords: C2541
ms.assetid: ed95180f-00df-4e62-a8e9-1b6dab8281bf
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 24bb63554f67d5496e46fb1ab8fa7133fadc38c5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2541"></a>C2541 chyby kompilátoru
'delete': odstranění: nelze odstranit objekty, které nejsou ukazatele  
  
 [Odstranit](../../cpp/delete-operator-cpp.md) operátor byl použit v objektu, který není ukazatel.  
  
 Následující ukázka generuje C2541:  
  
```  
// C2541.cpp  
int main() {  
   int i;  
   delete i;   // C2541 i not a pointer  
  
   // OK  
   int *ip = new int;  
   delete ip;  
}  
```
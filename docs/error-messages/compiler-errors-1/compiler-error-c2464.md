---
title: "C2464 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2464
dev_langs: C++
helpviewer_keywords: C2464
ms.assetid: ace953d6-b414-49ee-bfef-90578a8da00c
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7e2600608ae490363d9042ad72ad91bf7cfe32d2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2464"></a>C2464 chyby kompilátoru
"identifikátor": nelze použít, nové přidělit odkaz  
  
 Identifikátor odkazu byl přidělen s `new` operátor. Odkazy nejsou objekty paměti, takže `new` nemůže vrátit ukazatel na ně. Pomocí syntaxe standardní deklarace proměnné deklarovat odkaz.  
  
 Následující ukázka generuje C2464:  
  
```  
// C2464.cpp  
int main() {  
   new ( int& ir );   // C2464  
}  
```
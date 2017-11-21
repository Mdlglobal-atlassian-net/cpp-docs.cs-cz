---
title: "Kompilátoru (úroveň 4) upozornění C4032 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4032
dev_langs: C++
helpviewer_keywords: C4032
ms.assetid: 70dd0c85-0239-43f9-bb06-507f6a57d206
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 67700d14ef76b0b2f80621b18b6e4b1e469925a4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4032"></a>C4032 kompilátoru upozornění (úroveň 4)
formální parametr "číslo" je jiného typu povýšení  
  
 Typ parametru není kompatibilní, prostřednictvím výchozí povýšení s typem v předchozí deklaraci.  
  
 Jedná se o chybu v ANSI C ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) a upozornění v části rozšíření Microsoft (/Ze).  
  
## <a name="example"></a>Příklad  
  
```  
// C4032.c  
// compile with: /W4  
void func();  
void func(char);   // C4032, char promotes to int  
  
int main()  
{  
}  
```
---
title: "Kompilátoru (úroveň 2) upozornění C4094 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4094
dev_langs: C++
helpviewer_keywords: C4094
ms.assetid: e68929fb-3a1c-4be7-920b-d5f79f534f99
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 01b52b13876e30528632dec13dbaee60acf886fc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-2-c4094"></a>C4094 kompilátoru upozornění (úroveň 2)
vyžadující 'tokenu' deklarovaný žádné symboly  
  
 Kompilátor zjištěna deklarace prázdný využitím vyžadující struktury, sjednocení nebo třída. Deklaraci se ignoruje.  
  
## <a name="example"></a>Příklad  
  
```  
// C4094.cpp  
// compile with: /W2  
struct  
{  
};   // C4094  
  
int main()  
{  
}  
```  
  
 Tato podmínka, vygeneruje se chyba pod kompatibility ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).
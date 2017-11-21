---
title: "Kompilátoru (úroveň 4) upozornění C4232 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4232
dev_langs: C++
helpviewer_keywords: C4232
ms.assetid: f92028a5-4ddd-43c1-97f5-4f724e5e14af
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ae768c40ceca96da8c9f1b933d7006d08ed5e6e3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4232"></a>C4232 kompilátoru upozornění (úroveň 4)
nestandardní rozšíření používané: "identifikátor": adresa dllimport 'dllimport' nejsou statické, identity není zaručena.  
  
 V části rozšíření Microsoft (/Ze), můžete udělit nestatické hodnotu jako adresu funkce deklarovat s **dllimport** modifikátor. V části kompatibility ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)), to způsobí, že k chybě.  
  
 Následující ukázka generuje C4232:  
  
```  
// C4232.c  
// compile with: /W4 /Ze /c  
int __declspec(dllimport) f();  
int (*pfunc)() = &f;   // C4232  
```
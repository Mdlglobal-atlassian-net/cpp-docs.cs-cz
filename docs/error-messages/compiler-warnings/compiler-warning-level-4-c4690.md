---
title: "Kompilátoru (úroveň 4) upozornění C4690 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4690
dev_langs: C++
helpviewer_keywords: C4690
ms.assetid: 080a0ea1-458b-477b-a37a-4a34c94709ff
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9bf90ed2f977dfa0645458d17f6399984b6a8267
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4690"></a>C4690 kompilátoru upozornění (úroveň 4)
[emitidl – (pop)]: více bodů POP než nabízených oznámení  
  
 [Emitidl –](../../windows/emitidl.md) atribut byl odebrány jeden více času, který se instaluje.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4690.  
  
```  
// C4690.cpp  
// compile with: /c /W4  
[emitidl(pop)];   // C4690  
class x {};  
```
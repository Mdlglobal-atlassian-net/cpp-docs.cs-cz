---
title: "Kompilátoru (úroveň 1) upozornění C4606 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4606
dev_langs: C++
helpviewer_keywords: C4606
ms.assetid: c1b45fb6-672b-42eb-9e1c-c67b3e4150d3
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8cabc2eb00cb1944a19ac31b5f0f30deb3857c04
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4606"></a>C4606 kompilátoru upozornění (úroveň 1)
\#– Direktiva pragma upozornění: warning_number ignorován; Upozornění analýzy kódu nejsou přidružené úrovně varování  
  
 Analýza kódu, pouze upozornění `error`, `once`, a `default` jsou podporovány [upozornění](../../preprocessor/warning.md) – Direktiva pragma.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4606.  
  
```  
// C4606.cpp  
// compile with: /c /W1  
#pragma warning(1: 6001)   // C4606  
#pragma warning(once: 6001)   // OK  
```
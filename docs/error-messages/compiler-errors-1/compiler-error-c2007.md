---
title: "C2007 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2007
dev_langs:
- C++
helpviewer_keywords:
- C2007
ms.assetid: ecd09d99-5036-408b-9e46-bc15488f049e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aca1bc7436905dd7247ad797f47a5b44c8e52993
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2007"></a>C2007 chyby kompilátoru
\#definování syntaxe  
  
 Žádný identifikátor se zobrazí po `#define`. Chcete-li vyřešit chyby, použijte identifikátor.  
  
 Následující ukázka generuje C2007:  
  
```  
// C2007.cpp  
#define   // C2007  
```  
  
 Možná řešení:  
  
```  
// C2007b.cpp  
// compile with: /c  
#define true 1  
```
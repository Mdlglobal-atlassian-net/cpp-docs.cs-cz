---
title: "Kompilátoru (úroveň 4) upozornění C4019 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4019
dev_langs: C++
helpviewer_keywords: C4019
ms.assetid: 4ecfe85d-673f-4334-8154-36fe7f0b3444
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2528ec64644a6624e1dc4ffd633ba1f2c228a222
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4019"></a>C4019 kompilátoru upozornění (úroveň 4)
prázdný příkaz v globálním oboru  
  
 Příkaz není před středníkem v globálním oboru.  
  
 Pokud odeberete navíc středník, může být stanovena toto upozornění.  
  
## <a name="example"></a>Příklad  
  
```  
// C4019.c  
// compile with: /Za /W4  
#define declint( varname ) int varname;  
declint( a );   // C4019, int a;;  
declint( b )   // OK, int b;  
  
int main()  
{  
}  
```
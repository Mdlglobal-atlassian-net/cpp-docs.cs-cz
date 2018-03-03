---
title: "Kompilátoru (úroveň 1) upozornění C4364 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4364
dev_langs:
- C++
helpviewer_keywords:
- C4364
ms.assetid: 1477634c-d60f-4570-ad16-1aaeae24ac7f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9d532ff9cc030c92543bec898f34daf3559531f6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4364"></a>C4364 kompilátoru upozornění (úroveň 1)
\#použití pro sestavení 'file' dříve zobrazit při location(line_number) bez as_friend atributu. nebyly použity as_friend  
  
 A `#using` – direktiva se opakuje pro daná metadata souboru, ale `as_friend` kvalifikátor nebyl použit v první výskyt, kompilátor bude ignorovat druhý `as_friend`.  
  
 Další informace najdete v tématu [přátelských sestavení (C++)](../../dotnet/friend-assemblies-cpp.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří komponentu.  
  
```  
// C4364.cpp  
// compile with: /clr /LD  
ref class A {};  
```  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4364.  
  
```  
// C4364_b.cpp  
// compile with: /clr /W1 /c  
#using " C4364.dll"  
#using " C4364.dll" as_friend   // C4364  
```
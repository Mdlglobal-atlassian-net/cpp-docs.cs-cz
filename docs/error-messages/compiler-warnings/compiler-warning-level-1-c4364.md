---
title: Kompilátoru (úroveň 1) upozornění C4364 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4364
dev_langs:
- C++
helpviewer_keywords:
- C4364
ms.assetid: 1477634c-d60f-4570-ad16-1aaeae24ac7f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fb3bfb8075d618a6d2ea9b733b01d8b456fdc0e7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
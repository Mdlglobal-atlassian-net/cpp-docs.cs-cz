---
title: "Kompilátoru (úroveň 2) upozornění C4396 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4396
dev_langs:
- C++
helpviewer_keywords:
- C4396
ms.assetid: 7cd6b283-db17-4574-b299-03e0b913ad70
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bd40c2b78c12cff4b3904348c86dff1c7c3da0b9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-2-c4396"></a>C4396 kompilátoru upozornění (úroveň 2)
"název": specifikátor vložené nelze použít, když deklaraci friend odkazuje specializace šablony funkcí  
  
 Specializace šablony funkcí nelze zadat některé z [vložené](../../cpp/inline-functions-cpp.md) specifikátory. Kompilátor vydá upozornění C4396 a ignoruje specifikátor vložené.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Odeberte `inline`, `__inline`, nebo `__forceinline` specifikátor z deklarace funkce friend.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje kód neplatný friend deklaraci s funkce `inline` specifikátor.  
  
```  
// C4396.cpp  
// compile with: /W2 /c  
  
class X;   
template<class T> void Func(T t, int i);  
  
class X {  
    friend inline void Func<char>(char t, int i);  //C4396  
// try the following line instead  
//    friend void Func<char>(char t, int i);   
    int i;  
};  
```
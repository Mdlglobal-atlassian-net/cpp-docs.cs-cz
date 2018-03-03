---
title: "C2603 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2603
dev_langs:
- C++
helpviewer_keywords:
- C2603
ms.assetid: 9ca520d0-f082-4b65-933d-17c3bcf8b02c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c06c5747a3d785242e8b926fe6e1eaa251a2d8b4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2603"></a>C2603 chyby kompilátoru  
  
> '*funkce*': příliš mnoho bloku oboru statické objekty s konstruktor/destruktory ve funkci  
  
Ve verzích Visual C++ compiler před Visual Studio 2015 nebo když [/Zc:threadSafeInit-](../../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md) – možnost kompilátoru je zadán, je omezena 31 na počet statických objektů může mít v externě viditelné vložená funkce .  
  
Chcete-li vyřešit tento problém, doporučujeme použít novější verzi sady nástrojů kompilátoru Visual C++, nebo pokud je to možné, odeberte možnost kompilátoru /Zc:threadSafeInit-. Pokud to není možné, zvažte, kombinace statické objekty. Pokud jsou objekty stejného typu, zvažte použití jedné statické pole daného typu a odkazovat na jednotlivé členy podle potřeby.
  
## <a name="example"></a>Příklad  
  
Následující kód vytvoří C2603 a ukazuje jeden ze způsobů a opravte ji:  
  
```cpp  
// C2603.cpp  
// Compile by using: cl /W4 /c /Zc:threadSafeInit- C2603.cpp
struct C { C() {} };  
extern inline void f1() {  
    static C C01, C02, C03, C04, C05, C06, C07, C08, C09, C10;
    static C C11, C12, C13, C14, C15, C16, C17, C18, C19, C20;
    static C C21, C22, C23, C24, C25, C26, C27, C28, C29, C30, C31;  
    static C C32;   // C2603 Comment this line out to avoid error  
}  
```

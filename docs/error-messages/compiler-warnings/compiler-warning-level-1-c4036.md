---
title: "Kompilátoru (úroveň 1) upozornění C4036 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4036
dev_langs:
- C++
helpviewer_keywords:
- C4036
ms.assetid: f0b15359-4d62-48ec-8cb1-a7b36587a47f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c266e5148b908b6b3ecbc18ef6d34461767472b6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4036"></a>C4036 kompilátoru upozornění (úroveň 1)
Nepojmenované "typ" jako skutečný parametr  
  
 Není typu zadán název pro strukturu, union, výčet nebo třída používaná jako skutečný parametr. Pokud používáte [/Zg](../../build/reference/zg-generate-function-prototypes.md) generovat prototypy funkcí, kompilátor problémy toto upozornění a komentáře na typ formálního parametru v generované prototypu.  
  
 Zadejte název typu vyřešit toto upozornění.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4036.  
  
```  
// C4036.c  
// compile with: /Zg /W1  
// D9035 expected  
typedef struct { int i; } T;  
void f(T* t) {}   // C4036  
  
// OK  
typedef struct MyStruct { int i; } T2;  
void f2(T2 * t) {}  
```
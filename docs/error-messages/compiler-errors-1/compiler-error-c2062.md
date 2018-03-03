---
title: "C2062 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2062
dev_langs:
- C++
helpviewer_keywords:
- C2062
ms.assetid: 6cc98353-2ddf-43ab-88a2-9cc91cdd6033
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e4a006bed55f16e6ed94c3b5ed9415320acb86fc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2062"></a>C2062 chyby kompilátoru
typ "typ" neočekávané  
  
 Kompilátor neočekávali, název typu.  
  
 Následující ukázka generuje C2062:  
  
```  
// C2062.cpp  
// compile with: /c  
struct A {  : int l; };   // C2062  
struct B { private: int l; };   // OK  
```  
  
 C2062 může dojít také vzhledem ke způsobu kompilátor nedefinované typy obslužných rutin v seznamu parametrů konstruktor. Pokud kompilátor zaznamená typ nedefinované (překlepu?), předpokládá konstruktoru je výraz a problémy C2062. Chcete-li vyřešit, použijte pouze definovaných typů, v seznamu parametrů konstruktor.
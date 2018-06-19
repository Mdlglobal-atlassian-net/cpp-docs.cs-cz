---
title: C2062 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2062
dev_langs:
- C++
helpviewer_keywords:
- C2062
ms.assetid: 6cc98353-2ddf-43ab-88a2-9cc91cdd6033
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d11151a8e842796e4a5a8d45956782421daa1c70
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33168656"
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
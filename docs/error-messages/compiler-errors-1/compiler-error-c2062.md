---
title: "C2062 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2062
dev_langs: C++
helpviewer_keywords: C2062
ms.assetid: 6cc98353-2ddf-43ab-88a2-9cc91cdd6033
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 775923345052aba99b05f708c417b8bed267119b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
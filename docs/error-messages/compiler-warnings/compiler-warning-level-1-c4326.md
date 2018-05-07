---
title: Kompilátoru (úroveň 1) upozornění C4326 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4326
dev_langs:
- C++
helpviewer_keywords:
- C4326
ms.assetid: d44d2c4e-9456-42d3-b35b-4ba4b2d42ec7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 838c79d6ba897905dad18788adc5ee682ff2fa2c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4326"></a>C4326 kompilátoru upozornění (úroveň 1)
Návratový typ 'function' by měl být 'type1' místo 'type2'.  
  
 Funkce vrátil typ, jiné než ***type1***. Například pomocí [/Za](../../build/reference/za-ze-disable-language-extensions.md), hlavní nevrátil `int`.  
  
 Následující ukázka generuje C4326:  
  
```  
// C4326.cpp  
// compile with: /Za /W1  
char main()  
{   // C4326 try int main  
}  
```
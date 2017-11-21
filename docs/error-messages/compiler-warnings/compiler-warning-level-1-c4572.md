---
title: "Kompilátoru (úroveň 1) upozornění C4572 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4572
dev_langs: C++
helpviewer_keywords: C4572
ms.assetid: 482dee5a-29bd-4fc3-b769-9dfd4cd2a964
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4dad1236943c6055e0d40e139f83e4e7d90a555a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4572"></a>C4572 kompilátoru upozornění (úroveň 1)
Atribut [ParamArray] je zastaralá v/CLR, použijte "..." místo  
  
 Byl použit zastaralé styl zadat seznam argumentů s proměnnou. Při kompilaci pro modul CLR, použijte syntaxi třemi tečkami místo <xref:System.ParamArrayAttribute>. Další informace najdete v tématu [proměnné seznamy argumentů (...) (C + +/ CLI) ](../../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4572.  
  
```  
// C4572.cpp  
// compile with: /clr /W1  
void Func([System::ParamArray] array<int> ^);   // C4572  
void Func2(... array<int> ^){}   // OK  
  
int main() {  
   Func2(1, 2, 3);  
}  
```
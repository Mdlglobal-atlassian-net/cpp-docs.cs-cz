---
title: Kompilátoru (úroveň 4) upozornění C4565 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4565
dev_langs:
- C++
helpviewer_keywords:
- C4565
ms.assetid: a71f1341-a4a1-4060-ad1e-9322531883ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d3c4249783686c1fabb44395d3c092eca0d9230a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4565"></a>C4565 kompilátoru upozornění (úroveň 4)
'function': předefinování; symbol bylo dříve deklarované s __declspec(modifier)  
  
 Symbol předefinovat nebo předeklarována a druhý definice nebo deklarace, na rozdíl od první definice nebo deklarace, neměl `__declspec` – modifikátor (***modifikátor***). Toto upozornění je informační. Pokud chcete odstranit toto upozornění, odstraňte jednu z definice.  
  
 Následující ukázka generuje C4565:  
  
```  
// C4565.cpp  
// compile with: /W4 /LD  
__declspec(noalias) void f();  
void f();   // C4565  
```
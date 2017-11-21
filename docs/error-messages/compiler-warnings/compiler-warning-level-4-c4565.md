---
title: "Kompilátoru (úroveň 4) upozornění C4565 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4565
dev_langs: C++
helpviewer_keywords: C4565
ms.assetid: a71f1341-a4a1-4060-ad1e-9322531883ed
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2cbe5e8aecd8863f0b3ba092b8d199c1032ce157
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
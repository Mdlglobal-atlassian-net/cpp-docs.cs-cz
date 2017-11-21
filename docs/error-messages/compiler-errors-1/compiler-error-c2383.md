---
title: "C2383 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2383
dev_langs: C++
helpviewer_keywords: C2383
ms.assetid: 6696221d-879c-477a-a0f3-a6edc15fd3d7
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 20f6fa7626541f5fcd06bc2c2c513f52ec443ba4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2383"></a>C2383 chyby kompilátoru
'*symbol*': výchozí argumenty nejsou povoleny na tento symbol  
  
 Kompilátor C++ neumožňuje výchozí argumenty ukazatelů na funkce.  
  
 Tento kód byl přijat ve Visual C++ compiler ve verzi před Visual Studio 2005, ale teď obsahuje chybu. Pro kód, který funguje ve všech verzích Visual C++ nepřiřazujte výchozí hodnota pro argument ukazatel funkce.  
  
## <a name="example"></a>Příklad  
 Následující příklad generuje C2383 a zobrazuje možná řešení:  
  
```cpp  
// C2383.cpp  
// compile with: /c   
void (*pf)(int = 0);   // C2383  
void (*pf)(int);   // OK  
```
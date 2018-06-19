---
title: Kompilátoru (úroveň 1) upozornění C4176 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4176
dev_langs:
- C++
helpviewer_keywords:
- C4176
ms.assetid: cfffb934-219a-4a63-9df6-ba54405bf766
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f1e00e4bdc18b8adeb95d2425c8b122ffde867cd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33274859"
---
# <a name="compiler-warning-level-1-c4176"></a>C4176 kompilátoru upozornění (úroveň 1)
'podsoučásti': Neznámý podsoučásti pro součást prohlížeč #pragma  
  
 **Součást** – Direktiva pragma obsahuje neplatný podsoučásti. Pokud chcete vyloučit odkazy na konkrétní název, musíte použít **odkazy** možnost před název.  
  
## <a name="example"></a>Příklad  
  
```  
// C4176.cpp  
// compile with: /W1 /LD  
#pragma component(browser, off, i)  // C4176  
#pragma component(browser, off, references, i) // ok  
```
---
title: Kompilátoru (úroveň 1) upozornění C4651 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4651
dev_langs:
- C++
helpviewer_keywords:
- C4651
ms.assetid: f1ea82aa-4dc1-4972-b55a-57fdb962f0dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0015102a44b71f342b125532d20849590157ee0c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4651"></a>C4651 kompilátoru upozornění (úroveň 1)
definice zadány pro předkompilovaných hlaviček, ale ne pro aktuální kompilace  
  
 Definice byla zadána při generování předkompilovaných hlaviček, ale není v této kompilace.  
  
 Definice bude platit uvnitř předkompilovaných hlaviček, ale není ve zbývající části kódu.  
  
 Pokud předkompilovaných hlaviček byl sestaven s /DSYMBOL, kompilátor vygeneruje toto upozornění, pokud kompilace /Yu nemá /DSYMBOL.  Přidání /DSYMBOL do příkazového řádku /Yu přeloží toto upozornění.
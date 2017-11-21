---
title: "Kompilátoru (úroveň 1) upozornění C4651 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4651
dev_langs: C++
helpviewer_keywords: C4651
ms.assetid: f1ea82aa-4dc1-4972-b55a-57fdb962f0dd
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f1faffc6ba7b9df4fecefa3bef47f0418fdc8641
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4651"></a>C4651 kompilátoru upozornění (úroveň 1)
definice zadány pro předkompilovaných hlaviček, ale ne pro aktuální kompilace  
  
 Definice byla zadána při generování předkompilovaných hlaviček, ale není v této kompilace.  
  
 Definice bude platit uvnitř předkompilovaných hlaviček, ale není ve zbývající části kódu.  
  
 Pokud předkompilovaných hlaviček byl sestaven s /DSYMBOL, kompilátor vygeneruje toto upozornění, pokud kompilace /Yu nemá /DSYMBOL.  Přidání /DSYMBOL do příkazového řádku /Yu přeloží toto upozornění.
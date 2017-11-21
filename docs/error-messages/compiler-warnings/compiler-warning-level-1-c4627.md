---
title: "Kompilátoru (úroveň 1) upozornění C4627 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4627
dev_langs: C++
helpviewer_keywords: C4627
ms.assetid: 8840f3e6-b496-423a-8635-eb55d5f854a2
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7290a7b85be1c27fd33b11507bb2b2994ed5aaad
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4627"></a>C4627 kompilátoru upozornění (úroveň 1)
'\<identifikátor >': při vyhledávání předkompilované hlavičky použití přeskočen  
  
 Při vyhledávání pro umístění, kde se používá předkompilovaných hlaviček, kompilátor došlo `#include` direktivy pro  *\<identifikátor >* zahrnout soubor. Kompilátor ignoruje `#include` – direktiva, ale vydá upozornění **C4627** předkompilovaných hlaviček už neobsahuje-li  *\<identifikátor >* zahrnout soubor.  
  
## <a name="see-also"></a>Viz také  
 [Vytváření předkompilovaných hlavičkových souborů](../../build/reference/creating-precompiled-header-files.md)
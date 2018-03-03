---
title: "Kompilátoru (úroveň 1) upozornění C4627 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4627
dev_langs:
- C++
helpviewer_keywords:
- C4627
ms.assetid: 8840f3e6-b496-423a-8635-eb55d5f854a2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 66d199b8dede21f94a963113341eb6426f66a807
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4627"></a>C4627 kompilátoru upozornění (úroveň 1)
'\<identifikátor >': při vyhledávání předkompilované hlavičky použití přeskočen  
  
 Při vyhledávání pro umístění, kde se používá předkompilovaných hlaviček, kompilátor došlo `#include` direktivy pro  *\<identifikátor >* zahrnout soubor. Kompilátor ignoruje `#include` – direktiva, ale vydá upozornění **C4627** předkompilovaných hlaviček už neobsahuje-li  *\<identifikátor >* zahrnout soubor.  
  
## <a name="see-also"></a>Viz také  
 [Vytváření předkompilovaných hlavičkových souborů](../../build/reference/creating-precompiled-header-files.md)
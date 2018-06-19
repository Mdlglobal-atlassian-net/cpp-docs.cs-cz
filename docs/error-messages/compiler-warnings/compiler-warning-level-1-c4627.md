---
title: Kompilátoru (úroveň 1) upozornění C4627 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4627
dev_langs:
- C++
helpviewer_keywords:
- C4627
ms.assetid: 8840f3e6-b496-423a-8635-eb55d5f854a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dcde9e6707465fd95dbcb10e073a852624f0de0a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33284183"
---
# <a name="compiler-warning-level-1-c4627"></a>C4627 kompilátoru upozornění (úroveň 1)
'\<identifikátor >': při vyhledávání předkompilované hlavičky použití přeskočen  
  
 Při vyhledávání pro umístění, kde se používá předkompilovaných hlaviček, kompilátor došlo `#include` direktivy pro  *\<identifikátor >* zahrnout soubor. Kompilátor ignoruje `#include` – direktiva, ale vydá upozornění **C4627** předkompilovaných hlaviček už neobsahuje-li  *\<identifikátor >* zahrnout soubor.  
  
## <a name="see-also"></a>Viz také  
 [Vytváření předkompilovaných hlavičkových souborů](../../build/reference/creating-precompiled-header-files.md)
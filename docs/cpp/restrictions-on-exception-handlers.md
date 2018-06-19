---
title: Omezení obslužných rutin výjimek | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- restrictions, exception handlers
- exception handling [C++], exception handlers
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1f739152b502a156dc62dfab279e5ad044cfff99
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32420201"
---
# <a name="restrictions-on-exception-handlers"></a>Omezení obslužných rutin výjimek
Hlavním omezením použití obslužných rutin výjimek v kódu je nemožnost použít příkaz `goto` k přechodu do bloku příkazů `__try`. Místo toho je nutné vstoupit do tohoto bloku příkazů prostřednictvím normálního toku řízení. Z bloku příkazů `__try` lze přejít jinam a zanořovat obslužné rutiny výjimek dle libosti.  
  
## <a name="see-also"></a>Viz také  
 [Zápis obslužné rutiny výjimek](../cpp/writing-an-exception-handler.md)   
 [Strukturované zpracování výjimek (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
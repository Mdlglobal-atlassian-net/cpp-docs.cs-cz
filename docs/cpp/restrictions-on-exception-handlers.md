---
title: "Omezení obslužných rutin výjimek | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- restrictions, exception handlers
- exception handling [C++], exception handlers
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 42207a9bc1e9a355e6785a609ab0b130be063d55
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="restrictions-on-exception-handlers"></a>Omezení obslužných rutin výjimek
Hlavním omezením použití obslužných rutin výjimek v kódu je nemožnost použít příkaz `goto` k přechodu do bloku příkazů `__try`. Místo toho je nutné vstoupit do tohoto bloku příkazů prostřednictvím normálního toku řízení. Z bloku příkazů `__try` lze přejít jinam a zanořovat obslužné rutiny výjimek dle libosti.  
  
## <a name="see-also"></a>Viz také  
 [Zápis obslužné rutiny výjimek](../cpp/writing-an-exception-handler.md)   
 [Strukturované zpracování (C/C++) výjimek](../cpp/structured-exception-handling-c-cpp.md)
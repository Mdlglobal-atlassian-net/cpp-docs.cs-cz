---
title: "Podepsané bitové operace | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- bitwise operations
- signed bitwise operations
ms.assetid: 1e5cf65b-ee32-41a0-a5c2-82c1854091f6
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9ffc5335bb28e619f166a524083937d17a59bb97
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="signed-bitwise-operations"></a>Podepsané bitové operace
**ANSI 3.3** výsledky bitové operace na podepsaná celá čísla  
  
 Bitové operace s celými čísly se znaménkem fungují stejně jako bitové operace s celými čísly bez znaménka. Například `-16 & 99` může být vyjádřený v binární soubor jako  
  
```  
  11111111 11110000  
& 00000000 01100011  
  _________________  
  00000000 01100000  
```  
  
 Výsledkem bitové operace AND je 96.  
  
## <a name="see-also"></a>Viz také  
 [Celá čísla](../c-language/integers.md)
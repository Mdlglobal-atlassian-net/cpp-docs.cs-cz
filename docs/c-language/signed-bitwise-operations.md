---
title: "Podepsané bitové operace | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- bitwise operations
- signed bitwise operations
ms.assetid: 1e5cf65b-ee32-41a0-a5c2-82c1854091f6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 92750e2e309fd0ceaf06e81cc9483c0785795019
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
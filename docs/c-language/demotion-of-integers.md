---
title: "Degradace celých čísel | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: demoting integers
ms.assetid: 51fb3654-60b0-4de7-80eb-bd910086c18a
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 30af1eb47bc459cccf9ad08c36d05a3fe7b31bf8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="demotion-of-integers"></a>Degradace celých čísel
**ANSI 3.2.1.2** výsledek převodu na kratší znaménkem celé číslo nebo výsledek převodu celé číslo bez znaménka k znaménkem stejné délky, pokud hodnota není možné vyjádřit  
  
 Při **dlouho** celé číslo vložena do **malou**, nebo **krátké** vložena do `char`, jsou uchovány nejméně významným bajtů.  
  
 Například tento řádek  
  
```  
short x = (short)0x12345678L;  
```  
  
 přiřadí hodnotu 0x5678 do proměnné `x` a tento řádek  
  
```  
char y = (char)0x1234;  
```  
  
 přiřadí hodnotu 0x34 do proměnné `y`.  
  
 Když jsou proměnné se znaménkem převedeny na proměnné bez znaménka a naopak, zůstanou bitové vzory stejné. Například přetypování -2 (Bugcheck 0xFE) na nepodepsané hodnotu vypočítá 254 (také Bugcheck 0xFE).  
  
## <a name="see-also"></a>Viz také  
 [Celá čísla](../c-language/integers.md)
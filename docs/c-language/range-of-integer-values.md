---
title: "Rozsah celočíselné hodnoty | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 0e9c6161-8f3f-4bfb-9fcc-a6c8dc97d702
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5770c8efda6b044f99621d4a280e415fa825648f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="range-of-integer-values"></a>Rozsah hodnot typu Integer
**ANSI 3.1.2.5** reprezentace a nastaví hodnoty různých typů celých čísel  
  
 Celá čísla obsahovat 32bitová verze (čtyři bajtů). Celá čísla se znaménkem jsou reprezentována ve tvaru dvojkového doplňku. Nejvýznamnější bit uchovává znaménko: 1 pro záporné, 0 pro kladné a nulu. Hodnoty jsou uvedeny níže:  
  
|Typ|Minimální a maximální|  
|----------|-------------------------|  
|**short bez znaménka**|0 až 65535.|  
|`signed short`|-32768 až 32767|  
|`unsigned long`|0 do 4294967295|  
|**podepsané dlouho**|-do 2147483648 a 2147483647|  
  
## <a name="see-also"></a>Viz také  
 [Celá čísla](../c-language/integers.md)
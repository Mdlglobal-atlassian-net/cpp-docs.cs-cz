---
title: Rozsah celočíselné hodnoty | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 0e9c6161-8f3f-4bfb-9fcc-a6c8dc97d702
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2695b5d2a006529042453b7048bec400388fb74b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32385309"
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
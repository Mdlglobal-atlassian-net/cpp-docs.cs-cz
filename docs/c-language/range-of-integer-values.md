---
title: Rozsah hodnot typu Integer
ms.date: 11/04/2016
ms.assetid: 0e9c6161-8f3f-4bfb-9fcc-a6c8dc97d702
ms.openlocfilehash: bcf79877ed1bbd261a70b56d60df86adc31c897b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50632033"
---
# <a name="range-of-integer-values"></a>Rozsah hodnot typu Integer

**ANSI 3.1.2.5** reprezentace a sady hodnot z různých typů celých čísel

Celých čísel obsahovat 32 bitů (čtyř bajtů). Celá čísla se znaménkem jsou reprezentována ve tvaru dvojkového doplňku. Nejvýznamnější bit uchovává znaménko: 1 pro záporné, 0 pro kladné a nulu. Hodnoty jsou uvedeny níže:

|Typ|Minimální a maximální|
|----------|-------------------------|
|**short bez znaménka**|0 až 65535.|
|`signed short`|-32768 až 32767|
|`unsigned long`|0 na 4294967295|
|**podepsané dlouho**|-2147483648 do 2147483647.|

## <a name="see-also"></a>Viz také

[Celá čísla](../c-language/integers.md)
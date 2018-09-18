---
title: Rozsah celočíselných hodnot | Dokumentace Microsoftu
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
ms.openlocfilehash: d940824e6bb1dc728cb999c1e820cb7adcedf8ce
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092645"
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
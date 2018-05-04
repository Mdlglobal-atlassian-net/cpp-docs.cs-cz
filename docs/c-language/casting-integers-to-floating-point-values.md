---
title: Přetypování celých čísel na hodnoty s plovoucí desetinnou čárkou | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- integers, casting to floating-point values
ms.assetid: 81fd5b7d-15eb-4c11-a8c8-e1621ff54fd3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e00fdfc44c5939dbed2fb3258f0cab0023feeda0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="casting-integers-to-floating-point-values"></a>Přetypování celých čísel na hodnoty s plovoucí desetinnou čárkou
**ANSI 3.2.1.3** směr zkrácení při celé číslo je převedeno na číslo s plovoucí desetinnou čárkou, které nelze vyjádřit přesně původní hodnotu  
  
 Když je celé číslo přetypováno na hodnotu čísla s plovoucí desetinnou čárkou, které nemůže přesně představovat hodnotu, je tato hodnota zaokrouhlena (nahoru nebo dolů) na nejbližší vhodnou hodnotu.  
  
 Například přetypování **nepodepsané dlouho** (s 32 bity přesnosti) k **float** (jehož mantisa má 23 bity přesnost) Zaokrouhlí číslo na nejbližší násobek 256. **Dlouho** 4,294,966,913 k 4,294,967,167 hodnoty jsou zaokrouhleny na **float** hodnotu 4,294,967,040.  
  
## <a name="see-also"></a>Viz také  
 [Matematika s plovoucí desetinnou čárkou](../c-language/floating-point-math.md)
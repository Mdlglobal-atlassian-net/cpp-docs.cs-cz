---
title: Přetypování celých čísel na hodnoty s plovoucí desetinnou čárkou | Dokumentace Microsoftu
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
ms.openlocfilehash: a81b72a7dfedbc1d6033d53bde63be22943abb08
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46055218"
---
# <a name="casting-integers-to-floating-point-values"></a>Přetypování celých čísel na hodnoty s plovoucí desetinnou čárkou

**ANSI 3.2.1.3** směr zkrácení při převodu celého čísla na číslo s plovoucí desetinnou čárkou, které nemůže přesně představovat původní hodnotu

Když je celé číslo přetypováno na hodnotu čísla s plovoucí desetinnou čárkou, které nemůže přesně představovat hodnotu, je tato hodnota zaokrouhlena (nahoru nebo dolů) na nejbližší vhodnou hodnotu.

Například přetypování **unsigned long** (s 32 bity přesnosti) na **float** (jehož mantisa má 23 bitů přesnosti) zaokrouhlí toto číslo na nejbližší násobek 256. **Dlouhé** 4,294,966,913 k 4,294,967,167 hodnoty jsou zaokrouhleny na **float** hodnota 4,294,967,040.

## <a name="see-also"></a>Viz také

[Matematika s plovoucí desetinnou čárkou](../c-language/floating-point-math.md)
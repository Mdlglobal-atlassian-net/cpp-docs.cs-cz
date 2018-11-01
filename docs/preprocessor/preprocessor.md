---
title: Preprocesor
ms.date: 11/04/2016
helpviewer_keywords:
- preprocessor
ms.assetid: e120eda3-b413-49f1-a07c-e9fb128cf500
ms.openlocfilehash: bd139dcbbbe519cc4c9750a657f8b47c5a5bcd18
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530960"
---
# <a name="preprocessor"></a>Preprocesor
Preprocesor je textový procesor, který pracuje s textem zdrojového souboru v rámci první fáze překladu. Preprocesor neanalyzuje zdrojový text, ale rozdělí jej na tokeny za účelem vyhledání volání maker. Ačkoli kompilátor obvykle vyvolá preprocesor v první fázi, pro zpracování textu bez kompilace lze preprocesor vyvolat také samostatně.

Referenční materiál preprocesoru obsahuje následující oddíly:

- [Preprocesor – direktivy](../preprocessor/preprocessor-directives.md)

- [Operátory preprocesoru](../preprocessor/preprocessor-operators.md)

- [Předdefinovaná makra](../preprocessor/predefined-macros.md)

- [Pragmas](../preprocessor/pragma-directives-and-the-pragma-keyword.md)

**Specifické pro Microsoft**

Můžete získat seznam zdrojového kódu po předběžném zpracování pomocí [/E](../build/reference/e-preprocess-to-stdout.md) nebo [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) – možnost kompilátoru. Obě možnosti vyvolají preprocesor a způsobí zobrazení výsledného textu na standardním výstupním zařízení, které ve většině případů představuje konzole. Rozdíl mezi dvěma možnostmi je, že /E obsahuje direktivy `#line` a /EP tyto direktivy vyjme.

**Specifické pro END Microsoft**

##  <a name="_predir_special_terminology"></a> Speciální terminologie

V dokumentaci preprocesoru odkazuje termín „argument“ na entitu, která je předána funkci. V některých případech je upraven na „skutečný“ nebo „formální“, což popisuje výraz argumentu zadaný voláním funkce a deklaraci argumentu uvedenou v definici funkce.

Pojem „proměnná“ představuje jednoduchý datový objekt typu C. Pojem „objekt“ označuje objekty jazyka C++ a proměnné. Jedná se o inkluzivní termín.

## <a name="see-also"></a>Viz také

[C/C++ – referenční dokumentace preprocesoru](../preprocessor/c-cpp-preprocessor-reference.md)<br/>
[Fáze posunutí](../preprocessor/phases-of-translation.md)
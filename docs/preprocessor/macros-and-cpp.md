---
title: Makra a jazyk C++
ms.date: 11/04/2016
helpviewer_keywords:
- macros, C++
- macros
ms.assetid: 83a344c1-73c9-4ace-8b93-cccfb62c6133
ms.openlocfilehash: cd5d1237bc025cceb25cc290509b929b595a215f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50499889"
---
# <a name="macros-and-c"></a>Makra a jazyk C++
Jazyk C++ nabízí nové možnosti, z nichž některé nahrazují možnosti preprocesoru standardu ANSI C. Tyto nové možnosti zvyšují bezpečnost typů a předvídatelnost jazyka:

- V jazyce C++ lze objekty deklarované jako **const** lze použít v konstantních výrazech. To programům umožňuje deklarovat konstanty, které mají informace o typu a hodnotě, a výčty, které lze symbolicky zobrazit ladicím programem. Použití direktivy `#define` preprocesoru pro definování konstant není tak přesné. Pro není přiděleno žádné úložiště **const** objektu, pokud je výraz, který přijímá jeho adresu, nalezen v programu.

- Schopnost vložených funkcí jazyka C++ nahrazuje makra typů funkce. Výhody použití vložených funkcí oproti makrům jsou:

    - Bezpečnost typů. Vložené funkce jsou kontrolovány stejně jako normální funkce. Makra nejsou typově bezpečná.

    - Správná manipulace s argumenty, které mají vedlejší účinky. Vložené funkce vyhodnotí výrazy, které jsou zadány jako argumenty, před vstupem do těla funkce. Proto neexistuje možnost, že by výrazy s vedlejšími účinky byly nebezpečné.

Další informace o vložených funkcích naleznete v tématu [inline, __inline, \__forceinline](../cpp/inline-functions-cpp.md).

Z důvodu zpětné kompatibility jsou v jazyce C++ společnosti Microsoft zachovány všechny funkce preprocesoru, které existovaly ve standardu ANSI C a starších specifikacích jazyka C++.

## <a name="see-also"></a>Viz také

[Předdefinovaná makra](../preprocessor/predefined-macros.md)<br/>
[Makra (C/C++)](../preprocessor/macros-c-cpp.md)
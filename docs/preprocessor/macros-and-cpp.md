---
title: Makra a jazyk C++
ms.date: 08/29/2019
helpviewer_keywords:
- macros, C++
- macros
ms.assetid: 83a344c1-73c9-4ace-8b93-cccfb62c6133
ms.openlocfilehash: 8a86fb81544af91d4e844fb08b7948a589976e04
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220797"
---
# <a name="macros-and-c"></a>Makra a jazyk C++

C++nabízí nové funkce, z nichž některé supplant ty, které nabízí preprocesor jazyka ANSI C. Tyto nové možnosti zvyšují bezpečnost typů a předvídatelnost jazyka:

- V C++nástroji mohou být objekty deklarované jako const použity v konstantních výrazech. Umožňuje programům deklarovat konstanty, které mají informace o typu a hodnotě. Mohou deklarovat výčty, které lze zobrazit pomocí ladicího programu. Při použití `#define` direktivy preprocesoru k definování konstant není tak přesné a není typově bezpečná. Pro objekt **const** není přiděleno žádné úložiště, pokud program neobsahuje výraz, který přebírá svou adresu.

- Schopnost vložených funkcí jazyka C++ nahrazuje makra typů funkce. Výhody použití vložených funkcí oproti makrům jsou:

  - Bezpečnost typů. Vložené funkce jsou kontrolovány stejně jako normální funkce. Makra nejsou typově bezpečná.

  - Správná manipulace s argumenty, které mají vedlejší účinky. Vložené funkce vyhodnocují výrazy dodávané jako argumenty před zadáním těla funkce. Proto není nijak pravděpodobné, že by výraz s vedlejšími účinky byl nebezpečný.

Další informace o vložených funkcích naleznete v tématu [inline, __inline \_, _forceinline](../cpp/inline-functions-cpp.md).

Z důvodu zpětné kompatibility jsou v jazyce C++ společnosti Microsoft zachovány všechny funkce preprocesoru, které existovaly ve standardu ANSI C a starších specifikacích jazyka C++.

## <a name="see-also"></a>Viz také:

[Předdefinovaná makra](../preprocessor/predefined-macros.md)\
[Makra (C/C++)](../preprocessor/macros-c-cpp.md)

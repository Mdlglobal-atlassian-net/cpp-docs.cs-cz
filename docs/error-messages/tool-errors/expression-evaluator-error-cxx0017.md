---
title: Chyba při vyhodnocování výrazu CXX0017
ms.date: 11/04/2016
f1_keywords:
- CXX0017
helpviewer_keywords:
- CAN0017
- CXX0017
ms.assetid: af74db02-a64d-49ca-8363-3e044a107580
ms.openlocfilehash: bbf16ae9a503a8525edb42d6bf1fc4336c3f5267
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397130"
---
# <a name="expression-evaluator-error-cxx0017"></a>Chyba při vyhodnocování výrazu CXX0017

symbol se nenašel

Zadaný ve výrazu symbol se nenašel.

Jednou z možných příčin této chyby se neshoda velikosti písmen v názvu symbolu. Protože C a C++ jsou malá a velká písmena jazyky, musí být název symbolu uvedené v rozlišovat velikost písmen, ve kterém je definován ve zdroji.

Této chybě může dojít při pokusu o zadání proměnné, aby bylo možné sledovat proměnné během ladění. `typedef` Deklaruje nový název pro typ, ale nedefinuje nového typu. Typecast v ladicí program se pokusil vyžaduje název určitého typu.

Tato chyba se shoduje s CAN0017.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li vyřešit pomocí následujících možná řešení

1. Ujistěte se, že symbol je už deklarovaný v místě v programu, ve kterém se používá.

1. Použít název. skutečný typ pro přetypování proměnné v ladicím programu, spíše než `typedef`-definovaný název.
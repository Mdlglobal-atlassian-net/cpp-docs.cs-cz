---
title: Vyhodnocování výrazu CXX0017 chyba | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0017
dev_langs:
- C++
helpviewer_keywords:
- CAN0017
- CXX0017
ms.assetid: af74db02-a64d-49ca-8363-3e044a107580
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 431071137fb3f5b1b276327ee7d21f323ac24c5b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46136234"
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
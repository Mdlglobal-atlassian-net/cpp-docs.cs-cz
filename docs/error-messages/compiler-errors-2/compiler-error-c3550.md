---
title: Chyba kompilátoru C3550
ms.date: 11/04/2016
f1_keywords:
- C3550
helpviewer_keywords:
- C3550
ms.assetid: 9f2d5ffc-e429-41a1-89e3-7acc4fd47e14
ms.openlocfilehash: dbed14b9f2fa0f2163484edd8b5dfa330af9cbf1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498878"
---
# <a name="compiler-error-c3550"></a>Chyba kompilátoru C3550

v tomto kontextu je povolené jenom prosté zadání: decltype(auto).

Pokud `decltype(auto)` slouží jako zástupný symbol pro návratový typ funkce, musí být použit samostatně. Nelze použít jako součást deklarace ukazatelů (`decltype(auto*)`), deklarace odkazu (`decltype(auto&)`), nebo jakékoli jiné takové kvalifikace.

## <a name="see-also"></a>Viz také

[auto](../../cpp/auto-cpp.md)
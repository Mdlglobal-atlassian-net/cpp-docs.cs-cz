---
title: Chyba kompilátoru C3550
ms.date: 11/04/2016
f1_keywords:
- C3550
helpviewer_keywords:
- C3550
ms.assetid: 9f2d5ffc-e429-41a1-89e3-7acc4fd47e14
ms.openlocfilehash: 106ac93496eebb25ee603251d84680053e1310b7
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59032333"
---
# <a name="compiler-error-c3550"></a>Chyba kompilátoru C3550

v tomto kontextu je povolené jenom prosté zadání: decltype(auto).

Pokud `decltype(auto)` slouží jako zástupný symbol pro návratový typ funkce, musí být použit samostatně. Nelze použít jako součást deklarace ukazatelů (`decltype(auto*)`), deklarace odkazu (`decltype(auto&)`), nebo jakékoli jiné takové kvalifikace.

## <a name="see-also"></a>Viz také:

[auto](../../cpp/auto-cpp.md)
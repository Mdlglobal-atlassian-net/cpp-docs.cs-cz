---
title: Chyba kompilátoru C3550
ms.date: 11/04/2016
f1_keywords:
- C3550
helpviewer_keywords:
- C3550
ms.assetid: 9f2d5ffc-e429-41a1-89e3-7acc4fd47e14
ms.openlocfilehash: 106ac93496eebb25ee603251d84680053e1310b7
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59032333"
---
# <a name="compiler-error-c3550"></a>Chyba kompilátoru C3550

v tomto kontextu je povolené jenom prosté zadání: decltype(auto).

Pokud `decltype(auto)` slouží jako zástupný symbol pro návratový typ funkce, musí být použit samostatně. Nelze použít jako součást deklarace ukazatelů (`decltype(auto*)`), deklarace odkazu (`decltype(auto&)`), nebo jakékoli jiné takové kvalifikace.

## <a name="see-also"></a>Viz také:

[auto](../../cpp/auto-cpp.md)
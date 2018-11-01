---
title: Operátory přetypování
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], casting
- casting operators [C++]
ms.assetid: 16240348-26bc-4f77-8eab-57253f00ce52
ms.openlocfilehash: 4d6c8a0dc448e08ae2f344faeeb27756cdd27eff
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549744"
---
# <a name="casting-operators"></a>Operátory přetypování

Existuje několik operátorů přetypování specifických pro jazyk C++. Účelem těchto operátorů je odstranit některé nejasnosti a nebezpečí spojená s původními přetypováními jazyka C. Těmito operátory jsou:

- [přetypování dynamic_cast](../cpp/dynamic-cast-operator.md) používán pro převod polymorfních typů.

- [static_cast](../cpp/static-cast-operator.md) používán pro převod nepolymorfních typů.

- [const_cast](../cpp/const-cast-operator.md) slouží k odebrání **const**, **volatile**, a **__unaligned** atributy.

- [reinterpret_cast](../cpp/reinterpret-cast-operator.md) používá pro jednoduchou reinterpretaci bitů.

- [safe_cast](../windows/safe-cast-cpp-component-extensions.md) použít k tvorbě ověřitelného kódu MSIL.

Použití **const_cast** a **reinterpret_cast** jako poslední možnost, protože tyto operátory představují stejné nebezpečí jako stará přetypování. Pro úplné nahrazení starých přetypování jsou však stále zapotřebí.

## <a name="see-also"></a>Viz také:

[Přetypování](../cpp/casting.md)
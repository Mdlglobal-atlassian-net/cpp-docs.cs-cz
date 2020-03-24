---
title: Operátory přetypování
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], casting
- casting operators [C++]
ms.assetid: 16240348-26bc-4f77-8eab-57253f00ce52
ms.openlocfilehash: eac274a0207be675b8d13532c3110c6e71bd55c9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190095"
---
# <a name="casting-operators"></a>Operátory přetypování

Existuje několik operátorů přetypování specifických pro jazyk C++. Účelem těchto operátorů je odstranit některé nejasnosti a nebezpečí spojená s původními přetypováními jazyka C. Těmito operátory jsou:

- [dynamic_cast](../cpp/dynamic-cast-operator.md) Používá se pro převod polymorfních typů.

- [static_cast](../cpp/static-cast-operator.md) Používá se pro převod nepolymorfních typů.

- [const_cast](../cpp/const-cast-operator.md) Slouží k odebrání atributů **const**, **volatile**a **__unaligned** .

- [reinterpret_cast](../cpp/reinterpret-cast-operator.md) Používá se pro jednoduchou reinterpretaci bitů.

- [safe_cast](../extensions/safe-cast-cpp-component-extensions.md) Používá se C++v/CLI k výrobě ověřitelných MSIL.

Použijte **const_cast** a **reinterpret_cast** jako poslední možnost, protože tyto operátory představují stejné nebezpečí jako staré přetypování stylu. Pro úplné nahrazení starých přetypování jsou však stále zapotřebí.

## <a name="see-also"></a>Viz také

[Přetypování](../cpp/casting.md)

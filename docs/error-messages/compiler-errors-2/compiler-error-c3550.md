---
title: Chyba kompilátoru C3550
ms.date: 11/04/2016
f1_keywords:
- C3550
helpviewer_keywords:
- C3550
ms.assetid: 9f2d5ffc-e429-41a1-89e3-7acc4fd47e14
ms.openlocfilehash: 17c90aa68b29c9490deb8d49895162e8a6bdefec
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200769"
---
# <a name="compiler-error-c3550"></a>Chyba kompilátoru C3550

v tomto kontextu je povolené jenom jednoduché "decltype (auto)".

Pokud je `decltype(auto)` použito jako zástupný symbol pro návratový typ funkce, musí být použita samostatně. Nelze jej použít jako součást deklarace ukazatele (`decltype(auto*)`), deklaraci odkazu (`decltype(auto&)`) nebo jakékoli jiné takové kvalifikace.

## <a name="see-also"></a>Viz také

[auto](../../cpp/auto-cpp.md)

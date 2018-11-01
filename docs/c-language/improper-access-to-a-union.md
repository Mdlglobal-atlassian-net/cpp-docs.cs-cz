---
title: Nevhodný přístup ke sjednocení
ms.date: 11/04/2016
ms.assetid: b273d984-62a8-4003-9a87-bf0149d3f2dd
ms.openlocfilehash: a08f2c9aa76d0d2f2370dd45f9eb9ace77ceb76c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50642949"
---
# <a name="improper-access-to-a-union"></a>Nevhodný přístup ke sjednocení

**ANSI 3.3.2.3** člen sjednocení objektu se přistupuje pomocí členem jiného typu

Pokud je deklarována jako spojení dva typy a jedna hodnota je uložena, ale sjednocení je přistupováno pomocí jiného typu, nespolehlivé výsledky.

Například spojení **float** a `int` je deklarována. A **float** hodnota je uložena, ale program později přistupuje k hodnotě jako `int`. V takové situaci, hodnota bude trvat, závisí na vnitřní **float** hodnoty. Celočíselná hodnota nemusí být spolehlivé.

## <a name="see-also"></a>Viz také

[Struktury, sjednocení, výčty a bitová pole](../c-language/structures-unions-enumerations-and-bit-fields.md)
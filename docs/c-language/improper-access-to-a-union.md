---
title: Nevhodný přístup ke sjednocení
ms.date: 11/04/2016
ms.assetid: b273d984-62a8-4003-9a87-bf0149d3f2dd
ms.openlocfilehash: 9fd7bdc753f6359a8760e58813f9009411c1bf44
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151062"
---
# <a name="improper-access-to-a-union"></a>Nevhodný přístup ke sjednocení

**ANSI 3.3.2.3** člen sjednocení objektu se přistupuje pomocí členem jiného typu

Pokud je deklarována jako spojení dva typy a jedna hodnota je uložena, ale sjednocení je přistupováno pomocí jiného typu, nespolehlivé výsledky.

Například spojení **float** a `int` je deklarována. A **float** hodnota je uložena, ale program později přistupuje k hodnotě jako `int`. V takové situaci, hodnota bude trvat, závisí na vnitřní **float** hodnoty. Celočíselná hodnota nemusí být spolehlivé.

## <a name="see-also"></a>Viz také:

[Struktury, sjednocení, výčty a bitová pole](../c-language/structures-unions-enumerations-and-bit-fields.md)

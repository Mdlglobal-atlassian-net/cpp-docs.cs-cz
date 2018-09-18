---
title: Nevhodný přístup ke sjednocení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: b273d984-62a8-4003-9a87-bf0149d3f2dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2ac723ed80eaebc4b3f245ef56b761600007cd2d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028373"
---
# <a name="improper-access-to-a-union"></a>Nevhodný přístup ke sjednocení

**ANSI 3.3.2.3** člen sjednocení objektu se přistupuje pomocí členem jiného typu

Pokud je deklarována jako spojení dva typy a jedna hodnota je uložena, ale sjednocení je přistupováno pomocí jiného typu, nespolehlivé výsledky.

Například spojení **float** a `int` je deklarována. A **float** hodnota je uložena, ale program později přistupuje k hodnotě jako `int`. V takové situaci, hodnota bude trvat, závisí na vnitřní **float** hodnoty. Celočíselná hodnota nemusí být spolehlivé.

## <a name="see-also"></a>Viz také

[Struktury, sjednocení, výčty a bitová pole](../c-language/structures-unions-enumerations-and-bit-fields.md)
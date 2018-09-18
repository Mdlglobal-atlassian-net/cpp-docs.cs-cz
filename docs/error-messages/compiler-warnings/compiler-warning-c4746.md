---
title: Upozornění kompilátoru C4746 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
ms.assetid: 5e79ab46-6031-499a-a986-716c866b6c0e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5e6abce7ebbcdc41effed05ccf54337e3976c34e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054860"
---
# <a name="compiler-warning-c4746"></a>Upozornění kompilátoru C4746

přístup typu "\<výrazu >' / volatile: [iso&#124;ms] nastavení; zvažte použití vnitřních funkcí Using __iso_volatile_load/store.

C4746 je vygenerován pokaždé, když volatile proměnná je k nim přistupuje přímo. Jeho účelem je pomoci vývojářům při identifikaci umístění kódu, které jsou ovlivněny konkrétním model volatile aktuálně zadané (což se dá řídit pomocí [/volatile](../../build/reference/volatile-volatile-keyword-interpretation.md) – možnost kompilátoru). Zejména může být užitečné při hledání vygenerovaný kompilátorem hardwarové překážky paměti, když se používá /volatile:ms.

Vnitřní objekty Using __iso_volatile_load/store umožňuje explicitně přístup volatile paměti bez ovlivnění volatile model. Pomocí těchto vnitřních objektů, nebude spustí C4746.

Toto upozornění je vypnuto ve výchozím nastavení. Zobrazit [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.
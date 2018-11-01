---
title: Kompilátor upozornění (úroveň 4) C4710
ms.date: 11/04/2016
f1_keywords:
- C4710
helpviewer_keywords:
- C4710
ms.assetid: 76381ec7-3fc1-4bee-9a0a-c2c8307b92e2
ms.openlocfilehash: 0f8e66982192f8af6498c9151d32a44226e0560a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50487773"
---
# <a name="compiler-warning-level-4-c4710"></a>Kompilátor upozornění (úroveň 4) C4710

'function': funkce není vložena

Dané funkce byla vybrána pro vložené rozšíření, ale kompilátor neprovedli vkládání.

Vkládání se provádí na základě vlastního uvážení kompilátoru. **Vložené** – klíčové slovo, třeba **zaregistrovat** – klíčové slovo, se používají jako Nápověda pro kompilátor. Kompilátor používá heuristiku k určení, pokud by měl vložení funkce pro urychlení kódu při kompilaci pro rychlost, nebo pokud by měl vložení funkce zmenšit kód při kompilaci pro prostor. Kompilátor bude pouze vložené při kompilaci pro prostor velmi malé funkce.

V některých případech kompilátor nevloží určitou funkci mechanických důvodů. Zobrazit [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) seznam důvodů kompilátor může funkce.

Toto upozornění je vypnuto ve výchozím nastavení. Zobrazit [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.
---
title: Kompilátor upozornění (úroveň 1) C4656
ms.date: 11/04/2016
f1_keywords:
- C4656
helpviewer_keywords:
- C4656
ms.assetid: b5aaef74-2320-4345-a6ae-b813881a491c
ms.openlocfilehash: 4285ce20f6131c2503304ed1bdb1bde02b2efcec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665683"
---
# <a name="compiler-warning-level-1-c4656"></a>Kompilátor upozornění (úroveň 1) C4656

'symbol': datový typ je nový nebo se změnil od posledního sestavení nebo je někde definovaný nějak jinak

Přidat nebo změnit datový typ, takže nové ke zdrojovému kódu od posledního úspěšného sestavení. Upravit a pokračovat nepodporuje změny na stávající datové typy.

Toto upozornění bude vždy následovat [závažná chyba C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md). Další informace najdete v tématu [podporované změny kódu](/visualstudio/debugger/supported-code-changes-cpp).

### <a name="to-remove-this-warning-without-ending-the-current-debug-session"></a>Chcete-li odebrat toto upozornění bez ukončení aktuální relace ladění

1. Změna datového typu zpět do stavu před chybou.

1. Z **ladění** nabídce zvolte **použít změny kódu**.

### <a name="to-remove-this-error-without-changing-your-source-code"></a>Chcete-li odebrat tuto chybu beze změny zdrojového kódu

1. Z **ladění** nabídce zvolte **Zastavit ladění**.

1. Z **sestavení** nabídce zvolte **sestavení**.
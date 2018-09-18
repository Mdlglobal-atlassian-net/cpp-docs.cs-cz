---
title: Upozornění (úroveň 1) C4656 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4656
dev_langs:
- C++
helpviewer_keywords:
- C4656
ms.assetid: b5aaef74-2320-4345-a6ae-b813881a491c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3334b9448dd6e9d47ed0b3ee3e4dfb9dfc57b57f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032405"
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
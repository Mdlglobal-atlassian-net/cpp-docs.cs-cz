---
title: Upozornění kompilátoru (úroveň 1) C4655
ms.date: 08/27/2018
f1_keywords:
- C4655
helpviewer_keywords:
- C4655
ms.assetid: 540f2c7a-e4a1-49af-84b4-03eeea1bbf41
ms.openlocfilehash: d4c409c2d69099853a872142e05ef0fcda5a7655
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199528"
---
# <a name="compiler-warning-level-1-c4655"></a>Upozornění kompilátoru (úroveň 1) C4655

> '*symbol*': typ proměnné je od posledního sestavení nebo jiný definován jinde.

## <a name="remarks"></a>Poznámky

Od posledního úspěšného sestavení jste změnili nebo přidali nový datový typ. Upravit a pokračovat nepodporuje změny stávajících datových typů.

Toto upozornění je následováno [závažnou chybou C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md). Další informace najdete v článku [podporované změny kódu](/visualstudio/debugger/supported-code-changes-cpp).

### <a name="to-remove-this-warning-without-ending-the-current-debug-session"></a>Odebrání tohoto upozornění bez ukončení aktuální relace ladění

1. Před chybou změňte datový typ zpátky na jeho stav.

2. V nabídce **ladění** vyberte možnost **použít změny kódu**.

### <a name="to-remove-this-warning-without-changing-your-source-code"></a>Odebrání tohoto upozornění beze změny zdrojového kódu

1. V nabídce **ladění** vyberte možnost **Zastavit ladění**.

2. V nabídce **sestavení** klikněte na příkaz **sestavit**.

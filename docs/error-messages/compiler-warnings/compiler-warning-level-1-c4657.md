---
title: Upozornění kompilátoru (úroveň 1) C4657
ms.date: 11/04/2016
f1_keywords:
- C4657
helpviewer_keywords:
- C4657
ms.assetid: eb750050-cea6-4ead-b80c-d5dcd4971cfc
ms.openlocfilehash: 6cc049d99339a6f19ca86cd5c7a10f062a1451a9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199496"
---
# <a name="compiler-warning-level-1-c4657"></a>Upozornění kompilátoru (úroveň 1) C4657

výraz zahrnuje datový typ, který je od posledního sestavení nový.

Přidali jste nebo změnili datový typ, což je nového ve zdrojovém kódu od posledního úspěšného sestavení. Upravit a pokračovat nepodporuje změny stávajících datových typů.

Toto upozornění bude vždy následováno [závažnou chybou C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md). Další informace najdete v článku [podporované změny kódu](/visualstudio/debugger/supported-code-changes-cpp).

### <a name="to-remove-this-warning-without-ending-the-current-debug-session"></a>Odebrání tohoto upozornění bez ukončení aktuální relace ladění

1. Před chybou změňte datový typ zpátky na jeho stav.

1. V nabídce **ladění** vyberte možnost **použít změny kódu**.

### <a name="to-remove-this-error-without-changing-your-source-code"></a>Odstranění této chyby beze změny zdrojového kódu

1. V nabídce **ladění** vyberte možnost **Zastavit ladění**.

1. V nabídce **sestavení** klikněte na příkaz **sestavit**.

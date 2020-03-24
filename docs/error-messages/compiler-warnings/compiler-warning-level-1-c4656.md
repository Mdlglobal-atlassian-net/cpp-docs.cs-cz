---
title: Upozornění kompilátoru (úroveň 1) C4656
ms.date: 11/04/2016
f1_keywords:
- C4656
helpviewer_keywords:
- C4656
ms.assetid: b5aaef74-2320-4345-a6ae-b813881a491c
ms.openlocfilehash: a78da51a99aa924eadbf5c9f458ceb0a75889141
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175646"
---
# <a name="compiler-warning-level-1-c4656"></a>Upozornění kompilátoru (úroveň 1) C4656

' symbol ': datový typ je nový nebo se od posledního sestavení změnil, nebo je jinak definován jinde

Přidali jste nebo změnili datový typ, což je nového ve zdrojovém kódu od posledního úspěšného sestavení. Upravit a pokračovat nepodporuje změny stávajících datových typů.

Toto upozornění bude vždy následováno [závažnou chybou C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md). Další informace najdete v článku [podporované změny kódu](/visualstudio/debugger/supported-code-changes-cpp).

### <a name="to-remove-this-warning-without-ending-the-current-debug-session"></a>Odebrání tohoto upozornění bez ukončení aktuální relace ladění

1. Před chybou změňte datový typ zpátky na jeho stav.

1. V nabídce **ladění** vyberte možnost **použít změny kódu**.

### <a name="to-remove-this-error-without-changing-your-source-code"></a>Odstranění této chyby beze změny zdrojového kódu

1. V nabídce **ladění** vyberte možnost **Zastavit ladění**.

1. V nabídce **sestavení** klikněte na příkaz **sestavit**.

---
title: Závažná chyba C1092
ms.date: 11/04/2016
f1_keywords:
- C1092
helpviewer_keywords:
- C1092
ms.assetid: bcaa87f0-fbfc-4a33-844b-3b9f5d67f279
ms.openlocfilehash: af43ddb83e872762f720b156644e0d466957a8a7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203876"
---
# <a name="fatal-error-c1092"></a>Závažná chyba C1092

Upravit a pokračovat nepodporuje změny datových typů; požadováno sestavení

Změnili nebo jste přidali datový typ od posledního úspěšného sestavení.

- Příkaz Upravit a pokračovat nepodporuje změny stávajících datových typů, včetně definic třídy, struktury nebo výčtu. Je nutné zastavit ladění a sestavit aplikaci.

- Příkaz Upravit a pokračovat nepodporuje přidávání nových datových typů, pokud je soubor databáze programu, například VC*x*0. pdb (kde *x* je hlavní verze používaného vizuálu C++ ), jen pro čtení. Chcete-li přidat datové typy, kompilátor musí otevřít soubor PDB v režimu zápisu.

### <a name="to-remove-this-error-without-ending-the-current-debug-session"></a>Chcete-li odstranit tuto chybu bez ukončení aktuální relace ladění

1. Před chybou změňte datový typ zpátky na jeho stav.

1. V nabídce **ladění** vyberte možnost **použít změny kódu**.

### <a name="to-remove-this-error-without-changing-your-source-code"></a>Odstranění této chyby beze změny zdrojového kódu

1. V nabídce **ladění** vyberte možnost **Zastavit ladění**.

1. V nabídce **sestavení** klikněte na příkaz **sestavit**.

Další informace najdete v článku [podporované změny kódu](/visualstudio/debugger/supported-code-changes-cpp).

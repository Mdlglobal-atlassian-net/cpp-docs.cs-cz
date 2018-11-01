---
title: Závažná chyba C1092
ms.date: 11/04/2016
f1_keywords:
- C1092
helpviewer_keywords:
- C1092
ms.assetid: bcaa87f0-fbfc-4a33-844b-3b9f5d67f279
ms.openlocfilehash: 3268e5b124be40313bdc97b4c95d935ddd4f9160
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462722"
---
# <a name="fatal-error-c1092"></a>Závažná chyba C1092

Upravit a pokračovat nepodporuje změny datových typů; požadované sestavení

Změnily nebo přibyly typ dat od posledního úspěšného sestavení.

- Upravit a pokračovat nepodporuje změny na stávající datové typy, včetně definice třídy, struktury nebo výčtu. Musíte Zastavit ladění a sestavení aplikace.

- Upravit a pokračovat nepodporuje přidání nové datové typy, pokud soubor databáze programu, jako je například vc*x*0 pdb (kde *x* je hlavní verze Visual C++ používá) je jen pro čtení. Chcete-li přidat datové typy, musí kompilátor otevřete soubor typu .pdb v režimu zápisu.

### <a name="to-remove-this-error-without-ending-the-current-debug-session"></a>Chcete-li odebrat tuto chybu bez ukončení aktuální relace ladění

1. Změna datového typu zpět do stavu před chybou.

1. Z **ladění** nabídce zvolte **použít změny kódu**.

### <a name="to-remove-this-error-without-changing-your-source-code"></a>Chcete-li odebrat tuto chybu beze změny zdrojového kódu

1. Z **ladění** nabídce zvolte **Zastavit ladění**.

1. Z **sestavení** nabídce zvolte **sestavení**.

Další informace najdete v tématu [podporované změny kódu](/visualstudio/debugger/supported-code-changes-cpp).
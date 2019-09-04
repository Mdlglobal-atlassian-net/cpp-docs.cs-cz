---
title: 'Návod: Testování projektu (C++)'
ms.date: 04/25/2019
helpviewer_keywords:
- project testing [C++]
- testing projects
- projects [C++], testing
ms.assetid: 88cdd377-c5c8-4201-889d-32f5653ebead
ms.openlocfilehash: e0422b4f862b5438a313e25dac421d591bbbb9a5
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70273702"
---
# <a name="walkthrough-testing-a-project-c"></a>Návod: Testování projektu (C++)

Když spustíte program v režimu ladění, můžete pomocí zarážek pozastavit program a ověřit stav proměnných a objektů.

V tomto návodu sledujete hodnotu proměnné při spuštění programu a odvodit, proč hodnota není to, co byste očekávali.

## <a name="prerequisites"></a>Požadavky

- Tento návod předpokládá, že rozumíte základům C++ jazyka.

- Také předpokládá, že jste dokončili předchozí související návody, které jsou uvedeny v [části použití integrovaného vývojového prostředí C++ (IDE) sady Visual Studio pro desktopový vývoj](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

### <a name="to-run-a-program-in-debug-mode"></a>Spuštění programu v režimu ladění

1. Otevřete hry. cpp pro úpravy.

1. Vyberte tento řádek kódu:

   `Cardgame solitaire(1);`

1. Chcete-li nastavit zarážku na tomto řádku, v panelu nabídek vyberte možnost **ladit** > **přepínací zarážku**nebo vyberte klávesu **F9** . Nalevo od řádku se zobrazí červený kroužek. indikuje, že je nastavená zarážka. Chcete-li odebrat zarážku, můžete znovu zvolit příkaz nabídky nebo klávesu **F9** .

   Pokud používáte myš, můžete také nastavit nebo odebrat zarážku kliknutím na levý okraj.

1. Na panelu nabídek vyberte **ladit** > **Spustit ladění**nebo stiskněte klávesu **F5** .

   Když program dosáhne řádku, který má zarážku, spuštění se dočasně zastaví, protože váš program je v režimu přerušení. Žlutá šipka vlevo od řádku kódu indikuje, že se jedná o další řádek, který se má provést.

1. Chcete-li prošetřit hodnotu `Cardgame::totalParticipants` proměnné, přesuňte `Cardgame` ukazatel myši na ovládací prvek rozšíření na levé straně okna s popisem tlačítka. Zobrazí se název `totalParticipants` proměnné a její hodnota **12** .

   Otevřete místní nabídku pro `Cardgame::totalParticipants` proměnnou a zvolte možnost **Přidat kukátko** a zobrazte tuto proměnnou v okně **kukátko 1** . Můžete také zvýraznit proměnnou a přetáhnout ji do okna **kukátko 1** .

1. Chcete-li přejít na další řádek kódu, v řádku nabídek vyberte možnost **ladit** > **Krok přes**nebo vyberte klávesu **F10** .

   Hodnota `Cardgame::totalParticipants` v okně **kukátko 1** se teď zobrazí jako **13**.

1. Otevřete místní nabídku pro `return 0;` příkaz a zvolte možnost **Spustit ke kurzoru**. Žlutá šipka nalevo od kódu ukazuje na další příkaz, který má být proveden.

1. Číslo by mělo být zmenšeno `Cardgame` na konci. `Cardgame::totalParticipants` V `Cardgame::totalParticipants` tomto okamžiku by se měla rovnat 0, `Cardgame` protože všechny instance byly odstraněny, ale okno **kukátko 1** označuje `Cardgame::totalparticipants` , že se rovná **18**. Rozdíl značí, že v kódu je chyba, kterou můžete zjistit a opravit provedením dalšího návodu, [návodu: Ladění projektu (](../ide/walkthrough-debugging-a-project-cpp.md)C++).

1. Chcete-li program zastavit, v panelu nabídek klikněte na položku **ladit** > **Zastavit ladění**nebo vyberte klávesovou zkratku **SHIFT**+**F5** .

## <a name="next-steps"></a>Další kroky

**Předchozí** [Návod: Sestavení projektu (C++)](../ide/walkthrough-building-a-project-cpp.md)<br/>
**Generace** [Návod: Ladění projektu (C++)](../ide/walkthrough-debugging-a-project-cpp.md)

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Projekty a systémy sestavení](../build/projects-and-build-systems-cpp.md)<br/>

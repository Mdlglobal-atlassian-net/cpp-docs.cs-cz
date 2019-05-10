---
title: 'Návod: Testování projektu (C++)'
ms.date: 04/25/2019
helpviewer_keywords:
- project testing [C++]
- testing projects
- projects [C++], testing
ms.assetid: 88cdd377-c5c8-4201-889d-32f5653ebead
ms.openlocfilehash: 5ced3c4267f2c33869e18373c11ebf5e237d9485
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857657"
---
# <a name="walkthrough-testing-a-project-c"></a>Návod: Testování projektu (C++)

Když spustíte program v režimu ladění, můžete používat zarážky pro pozastavení programu a kontrolu stavu proměnných a objektů.

V tomto podrobném návodu sledovat hodnotu proměnné po spuštění programu a zjistit, proč hodnota není, co očekáváte.

## <a name="prerequisites"></a>Požadavky

- Tento názorný průvodce předpokládá, že chápete základy jazyka C++.

- Dále předpokládá, že jste dokončili dříve související návody, které jsou uvedeny v [pomocí integrovaného vývojového prostředí sady Visual Studio pro vývoj v jazyce C++ Desktop](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

### <a name="to-run-a-program-in-debug-mode"></a>Spuštění programu v režimu ladění

1. Games.cpp otevřete pro úpravy.

1. Vyberte tento řádek kódu:

   `Cardgame.solitaire(1);`

1. Chcete-li nastavit zarážku na tomto řádku, na panelu nabídek zvolte **ladění** > **Přepnout zarážku**, nebo zvolte **F9** klíč. Zobrazí se červený kruh vlevo od řádku; znamená to, že byla nastavena zarážka. Chcete-li odebrat zarážku, můžete použít příkaz nabídky nebo **F9** klíč znovu.

   Pokud používáte myš, můžete také nastavit nebo odebrat zarážku kliknutím do levého okraje.

1. V panelu nabídky zvolte **ladění** > **spustit ladění**, nebo zvolte **F5** klíč.

   Když program dosáhne řádku se zarážkou, provádění se dočasně zastaví, protože aplikace je v režimu pozastavení. Žlutá šipka vlevo od řádku kódu označuje, že je na další řádek, který se spustí.

1. Chcete-li zkoumat hodnoty `Cardgame::totalParticipants` proměnnou, přesuňte ukazatel nad `Cardgame` a poté ho přesuňte nad rozšiřující ovládací prvek vlevo od okna popisu. Název proměnné `totalParticipants` a její hodnota **12** jsou zobrazeny.

   Otevřete místní nabídku `Cardgame::totalParticipants` proměnné a pak zvolte **Přidat kukátko** zobrazíte danou proměnnou v **kukátko 1** okna. Můžete také zvýraznit proměnné a přetáhněte ji do **kukátko 1** okna.

1. Chcete-li na další řádek kódu na řádku nabídek zvolte **ladění** > **Krokovat s přeskočením**, nebo zvolte **F10** klíč.

   Hodnota `Cardgame::totalParticipants` v **kukátko 1** okno se teď zobrazí jako **13**.

1. Otevřete místní nabídku `return 0;` příkaz a klikněte na tlačítko **spustit ke kurzoru**. Žlutá šipka nalevo od kód odkazuje na další příkaz, který se spustí.

1. `Cardgame::totalParticipants` Čísla by měla snížit při `Cardgame` skončí. V tomto okamžiku `Cardgame::totalParticipants` by se měl rovnat 0, protože všechny `Cardgame` instancí se odstranily, ale **kukátko 1** okno znamená, že `Cardgame::totalparticipants` rovná **18**. Rozdíl označuje, že je chyba v kódu, který lze rozpoznat a opravit provedením dalšího názorného postupu, [názorný postup: Ladění projektu (C++)](../ide/walkthrough-debugging-a-project-cpp.md).

1. Chcete-li ukončit program, na panelu nabídek, zvolte **ladění** > **Zastavit ladění**, nebo zvolte **Shift**+**F5**klávesové zkratky.

## <a name="next-steps"></a>Další kroky

**Předchozí:** [Návod: Sestavení projektu (C++)](../ide/walkthrough-building-a-project-cpp.md)<br/>
**Další:** [Návod: Ladění projektu (C++)](../ide/walkthrough-debugging-a-project-cpp.md)<br/>

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Projekty a systémy sestavení](../build/projects-and-build-systems-cpp.md)<br/>

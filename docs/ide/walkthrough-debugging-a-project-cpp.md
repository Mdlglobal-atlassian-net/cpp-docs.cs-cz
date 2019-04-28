---
title: 'Návod: Ladění projektu (C++)'
ms.date: 04/25/2019
helpviewer_keywords:
- projects [C++], debugging
- project debugging [C++]
- debugging projects
ms.assetid: a5cade77-ba51-4b03-a7a0-6897e3cd6a59
ms.openlocfilehash: 0a1ceddca3234ead7d10cc839d41a6d644ec1866
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349916"
---
# <a name="walkthrough-debugging-a-project-c"></a>Návod: Ladění projektu (C++)

V tomto návodu změníte program pro vyřešení problému, který jste zjistili při testování projektu.

## <a name="prerequisites"></a>Požadavky

- Tento názorný průvodce předpokládá, že chápete základy jazyka C++.

- Dále předpokládá, že jste dokončili dříve související návody, které jsou uvedeny v [pomocí integrovaného vývojového prostředí sady Visual Studio pro vývoj v jazyce C++ Desktop](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

### <a name="to-fix-a-program-that-has-a-bug"></a>Chcete-li vyřešit program, který obsahuje chybu

1. Chcete-li zjistit, co se stane, když je objekt `Cardgame` zničen, zobrazte destruktor třídy `Cardgame`.

   V panelu nabídky zvolte **zobrazení** > **zobrazení tříd**.

   V **zobrazení tříd** okna, rozbalte **hru** stromu projektu a vyberte **Cardgame** třídu členy třídy a metody.

   Otevřete místní nabídku **~Cardgame(void)** destruktor a klikněte na tlačítko **přejít k definici**.

1. Aby se snížila `totalParticipants` při ukončení Cardgame přidejte následující kód mezi otevírací a uzavírací závorky `Cardgame::~Cardgame` – destruktor.

   [!code-cpp[NVC_Walkthrough_Debugging_A_Project#110](../ide/codesnippet/CPP/walkthrough-debugging-a-project-cpp_1.cpp)]

1. Po změnách by, by měl vypadat Cardgame.cpp souboru následující kód:

   [!code-cpp[NVC_Walkthrough_Debugging_A_Project#111](../ide/codesnippet/CPP/walkthrough-debugging-a-project-cpp_2.cpp)]

1. V panelu nabídky zvolte **sestavení** > **sestavit řešení**.

1. Po dokončení sestavení spusťte je v režimu ladění pomocí možnosti **ladění** > **spustit ladění** na řádku nabídek nebo kliknutím **F5** klíč. Program se pozastaví na k první zarážce.

1. Chcete-li krokovat programem, v řádku nabídek zvolte **ladění** > **Krokovat s přeskočením**, nebo zvolte **F10** klíč.

   Všimněte si, že po každém z nich `Cardgame` provede konstruktor, hodnota `totalParticipants` zvyšuje. Když `PlayGames` funkce vrátí, protože každému `Cardgame` instance dostane mimo rozsah a je odstraněna (a je zavolán destruktor), `totalParticipants` snižuje. Těsně před `return` je proveden příkaz `totalParticipants` rovná 0.

1. Pokračujte v krokování programem, dokud se neukončí, nebo jej spusťte pomocí možnosti **ladění** > **spustit** na řádku nabídek nebo kliknutím **F5** klíč.

## <a name="next-steps"></a>Další kroky

**Předchozí:** [Návod: Testování projektu (C++)](../ide/walkthrough-testing-a-project-cpp.md)<br/>
**Další:** [Návod: Nasazení programu (C++)](../ide/walkthrough-deploying-your-program-cpp.md)<br/>

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Projekty a systémy sestavení](../build/projects-and-build-systems-cpp.md)<br/>

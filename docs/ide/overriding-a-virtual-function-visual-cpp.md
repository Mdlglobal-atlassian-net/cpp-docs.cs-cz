---
title: Přepisování virtuální funkce (Visual C++)
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.virtualfunc.override
helpviewer_keywords:
- virtual functions, overriding
- base classes, overriding virtual functions defined in
- Properties window, overriding virtual functions in
ms.assetid: 2d8c76f2-7a6b-4c9c-8de5-4282ce7755b6
ms.openlocfilehash: 193c84d2b9a0fe50ae84d3e69834feab27342042
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484134"
---
# <a name="overriding-a-virtual-function-visual-c"></a>Přepisování virtuální funkce (Visual C++)

Můžete přepsat virtuální funkce definované v základní třídě ze sady Visual Studio [okno vlastností](/visualstudio/ide/reference/properties-window).

### <a name="to-override-a-virtual-function-in-the-properties-window"></a>Chcete-li přepsat virtuální funkci v okně Vlastnosti

1. V zobrazení tříd klikněte na třídu.

1. V okně Vlastnosti klikněte na tlačítko **přepíše** tlačítko.

   > [!NOTE]
   >  **Přepíše** tlačítko je k dispozici při výběru názvu třídy v zobrazení tříd nebo když kliknete na okno zdrojového kódu.

   V levém sloupci jsou uvedeny virtuální funkce. Pokud název virtuální funkce se také zobrazí v pravém sloupci, pak přepsání již byl implementován.

1. Pokud funkce nemá žádné přepsání, pak klikněte na buňku v pravém sloupci v okně Vlastnosti, chcete-li zobrazit navrhovaný název funkce přepsat jako \<Přidat >*FuncName*.

1. Kliknutím na navrhovaný název přidat kód zástupných procedur pro funkci.

1. Chcete-li upravit přepisující funkce, dvakrát klikněte na název funkce v zobrazení tříd a úpravy kódu v okně zdroje.

Chcete-li odebrat přepsání, klikněte na název funkce přepsání v pravém sloupci a vyberte \<odstranit >*FuncName*. Je zakomentovaný, kód vaší funkce.

## <a name="see-also"></a>Viz také

[Přidání funkce pomocí průvodců kódem](../ide/adding-functionality-with-code-wizards-cpp.md)<br>
[Přidání třídy](../ide/adding-a-class-visual-cpp.md)<br>
[Přidání členské funkce](../ide/adding-a-member-function-visual-cpp.md)<br>
[Přidání členské proměnné](../ide/adding-a-member-variable-visual-cpp.md)<br>
[Popisovače zpráv knihovny MFC](../mfc/reference/adding-an-mfc-message-handler.md)<br>
[Navigace strukturou třídy](../ide/navigating-the-class-structure-visual-cpp.md)
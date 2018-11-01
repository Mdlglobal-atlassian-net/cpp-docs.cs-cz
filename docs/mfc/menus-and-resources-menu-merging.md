---
title: 'Nabídky a prostředky: Sloučení nabídky'
ms.date: 11/04/2016
helpviewer_keywords:
- status bars [MFC], OLE document applications
- visual editing [MFC], application menus and resources
- coordinating menu layouts [MFC]
- OLE containers [MFC], menus and resources
- toolbars [MFC], OLE document applications
- merging toolbar and status bar [MFC]
- menus [MFC], OLE document applications
ms.assetid: 80b6bb17-d830-4122-83f0-651fc112d4d1
ms.openlocfilehash: 30663afae0bfd30b42f99daf95cb8ff35979ee50
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438438"
---
# <a name="menus-and-resources-menu-merging"></a>Nabídky a prostředky: Sloučení nabídky

Tento článek podrobně popisuje kroky potřebné pro OLE – aplikace dokumentů zpracování vizuální úpravy a aktivace na místě správně. Aktivace na místě představuje výzvu pro kontejner a server aplikace (součást). Uživatel zůstane v okně rámce (v rámci dokumentu kontejneru), ale je ve skutečnosti spuštěna jiná aplikace (server). To vyžaduje koordinaci mezi prostředky kontejneru a serverové aplikace.

V tomto článku probíraná témata zahrnují:

- [Rozložení nabídek](#_core_menu_layouts)

- [Panely nástrojů a stavové řádky](#_core_toolbars_and_status_bars)

##  <a name="_core_menu_layouts"></a> Rozložení nabídek

Prvním krokem je koordinace rozložení nabídek. Další informace najdete v tématu **vytvoření nabídky** tématu [aspekty programování nabídky](https://msdn.microsoft.com/library/ms647557.aspx) v sadě Windows SDK.

Aplikace typu kontejner by měl vytvořit novou nabídku pro použití pouze v případě, že vložené položky se aktivují v místě. Minimálně by měla tato nabídka skládá z těchto možností v uvedeném pořadí:

1. Nabídka Soubor je stejný jako ten, který používá, když jsou otevřené soubory. (Obvykle žádné jiné položky nabídky jsou umístěny před na další položku.)

1. Dvě po sobě jdoucích oddělovače.

1. Nabídka okna stejný jako ten, který používá, když jsou otevřené soubory (pouze tehdy, pokud aplikace typu kontejner v aplikaci MDI). Některé aplikace mohou mít jiné nabídky, jako je například nabídka možností, které patří do této skupiny, která zůstává v nabídce při aktivaci vloženou položku na místě.

    > [!NOTE]
    >  Můžou existovat jiných nabídek, které ovlivňují zobrazení dokumentu kontejneru, jako je například přiblížení. Tyto nabídky kontejner se zobrazí mezi dvěma oddělovači v této nabídce prostředků.

Aplikace serveru (součásti) by měl také vytvořit novou nabídku speciálně pro aktivace na místě. Měla by být stejně jako nabídka používá, když jsou otevřené soubory, ale bez položky nabídky, jako je například soubor a okna, který manipulovat s dokumentu na serveru, ne data. Tato nabídka obvykle se skládá z následujících akcí:

1. Upravte nabídku stejný jako ten, který používá, když jsou otevřené soubory.

1. Oddělovač.

1. Upravování nabídky, jako je například nabídka pera v ukázkové aplikaci Scribble objektu.

1. Oddělovač.

1. Nabídka Nápověda.

Příklad podívejte se na rozložení některé ukázkové místní nabídky pro kontejner a serverem. Aby byl srozumitelnější příklad jsme odebrali podrobnosti o každé položky nabídky. V místní nabídce kontejneru obsahuje následující položky:

```
IDR_CONTAINERTYPE_CNTR_IP MENU PRELOAD DISCARDABLE
BEGIN
    POPUP "&File C1"
    MENUITEM SEPARATOR
    POPUP "&Zoom C2"
    MENUITEM SEPARATOR
    POPUP "&Options C3"
    POPUP "&Window C3"
END
```

Po sobě jdoucích oddělovače označují, kam by měly patřit první část nabídky na server. Nyní se podívejte na serveru místní nabídky:

```
IDR_SERVERTYPE_SRVR_IP MENU PRELOAD DISCARDABLE
BEGIN
    POPUP "&Edit S1"
    MENUITEM SEPARATOR
    POPUP "&Format S2"
    MENUITEM SEPARATOR
    POPUP "&Help S3"
END
```

Oddělovače tady označují, kam by měly patřit druhé skupině položky nabídky kontejner. Výsledný struktura nabídky při aktivaci objektu z tohoto serveru na místě uvnitř tohoto kontejneru vypadá takto:

```
BEGIN
    POPUP "&File C1"
    POPUP "&Edit S1"
    POPUP "&Zoom C2"
    POPUP "&Format S2"
    POPUP "&Options C3
    POPUP "&Window C3"
    POPUP "&Help S3"
END
```

Jak je vidět, oddělovače se nahradily pro různé skupiny nabídek každou aplikaci.

Serverové aplikace by měl být rovněž dodán tabulek akcelerátorů spojený s místní nabídkou. Kontejner je začlenit do vlastní tabulky akcelerátoru.

Při aktivaci vloženou položku na místě rozhraní načte v místní nabídce. Pak vyzve k zadání místní aktivace server žádosti o nabídku a vloží ho ve kterém jsou oddělovače. To je, jak zkombinovat nabídky. Získejte nabídky z kontejneru pro provozování na umístění souboru a okno a získat nabídky ze serveru pro položku.

##  <a name="_core_toolbars_and_status_bars"></a> Panely nástrojů a stavové řádky

Serverové aplikace by měl vytvořit nový panel nástrojů a uložte jeho rastrového obrázku v samostatném souboru. Aplikace vygenerované průvodcem aplikací uložte soubor s názvem ITOOLBAR tento rastrový obrázek. BMP. Nový panel nástrojů nahradí nástrojů aplikace typu kontejner položku pro váš server se aktivuje v místě, by měl obsahovat stejné položky jako normální nástrojů, ale odebrání ikony reprezentující překročení položek v nabídkách souboru a okno.

Tento panel nástrojů je načten do vaší `COleIPFrameWnd`-odvozené třídy za vás vytvoří služba Průvodce aplikací. Aplikace typu kontejner zpracovává stavový řádek. Další informace o implementace oken s rámečkem na místě, naleznete v tématu [servery: implementace serveru](../mfc/servers-implementing-a-server.md).

## <a name="see-also"></a>Viz také

[Nabídky a prostředky (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Aktivace](../mfc/activation-cpp.md)<br/>
[Servery](../mfc/servers.md)<br/>
[Kontejnery](../mfc/containers.md)


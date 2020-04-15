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
ms.openlocfilehash: 149af83bd53b7a97fd264bd6b18701fc9f64ea1f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364759"
---
# <a name="menus-and-resources-menu-merging"></a>Nabídky a prostředky: Sloučení nabídky

Tento článek podrobně popisuje kroky nezbytné pro aplikace dokumentu OLE správně zpracovat vizuální úpravy a aktivace na místě. Aktivace na místě představuje výzvu pro aplikace kontejneru i serveru (komponenty). Uživatel zůstane ve stejném okně rámce (v kontextu dokumentu kontejneru), ale ve skutečnosti běží jinou aplikaci (server). To vyžaduje koordinaci mezi prostředky kontejneru a serverových aplikací.

Témata uvedená v tomto článku zahrnují:

- [Rozložení nabídek](#_core_menu_layouts)

- [Panely nástrojů a stavové panely](#_core_toolbars_and_status_bars)

## <a name="menu-layouts"></a><a name="_core_menu_layouts"></a>Rozložení nabídek

Prvním krokem je koordinace rozložení nabídek. Kontejnerové aplikace by měly vytvořit novou nabídku, která se použije pouze při aktivaci vložených položek na místě. Toto menu by se mělo přinejmenším skládat z následujících, v uvedeném pořadí:

1. Nabídka souborů je shodná s nabídkou používanou při otevření souborů. (Obvykle nejsou před další položkou umístěny žádné jiné položky nabídky.)

1. Dva po sobě jdoucí oddělovače.

1. Nabídka okna shodná s nabídkou používanou při otevření souborů (pouze v případě, že aplikace kontejneru v aplikaci MDI). Některé aplikace mohou mít jiné nabídky, například nabídky Možnosti, které patří do této skupiny, která zůstává v nabídce, když je aktivována vložená položka na místě.

    > [!NOTE]
    >  Mohou existovat další nabídky, které ovlivňují zobrazení dokumentu kontejneru, například Lupa. Tyto nabídky kontejneru se zobrazí mezi dvěma oddělovači v této nabídce prostředku.

Serverové (komponentní) aplikace by také měly vytvořit novou nabídku speciálně pro aktivaci na místě. Mělo by to být jako nabídka používaná při otevření souborů, ale bez položek nabídky, jako je například Soubor a okno, které manipulují s dokumentem serveru namísto dat. Obvykle se tato nabídka skládá z následujících:

1. Upravit nabídku shodnou s nabídkou použitou při otevření souborů.

1. Oddělovač.

1. Nabídky pro úpravy objektů, například nabídka Pero v ukázkové aplikaci Klikyháky.

1. Oddělovač.

1. Nabídka Nápověda.

Například se podívejte na rozložení některých ukázkových místních nabídek pro kontejner a server. Podrobnosti o každé položce nabídky byly odebrány, aby byl příklad jasnější. Nabídka kontejneru na místě má následující položky:

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

Po sobě jdoucí oddělovače označují, kam by měla být uvedena první část nabídky serveru. Nyní se podívejte na menu serveru na místě:

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

Oddělovače zde označují, kde by měla jít druhá skupina položek nabídky kontejneru. Výsledná struktura nabídky, když je objekt z tohoto serveru aktivován na místě uvnitř tohoto kontejneru, vypadá takto:

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

Jak můžete vidět, oddělovače byly nahrazeny různými skupinami nabídky každé aplikace.

Akcelerátortabulky spojené s místní nabídkou by měly být také dodávány serverovou aplikací. Kontejner je začlení do svých vlastních tabulek akcelerátorů.

Když je aktivována vložená položka na místě, rozhraní načte místní nabídku. Poté požádá serverovou aplikaci o nabídku pro aktivaci na místě a vloží ji tam, kde jsou oddělovače. Takto se menu kombinují. Získáte nabídky z kontejneru pro provoz na soubor a umístění okna a dostanete nabídky ze serveru pro provoz na položku.

## <a name="toolbars-and-status-bars"></a><a name="_core_toolbars_and_status_bars"></a>Panely nástrojů a stavové panely

Serverové aplikace by měly vytvořit nový panel nástrojů a uložit jeho bitmapu do samostatného souboru. Aplikace generované průvodcem ukládají tuto bitmapu do souboru s názvem ITOOLBAR. Bmp. Nový panel nástrojů nahradí panel nástrojů aplikace kontejneru, když je položka serveru aktivována na místě, a měl by obsahovat stejné položky jako běžný panel nástrojů, ale odebrat ikony představující položky v nabídkách Soubor a Okno.

Tento panel nástrojů je `COleIPFrameWnd`načten do vaší odvozené třídy, kterou pro vás vytvořil průvodce aplikací. Stavový řádek je zpracován aplikací kontejneru. Další informace o implementaci oken rámce na místě naleznete v tématu [Servery: Implementace serveru](../mfc/servers-implementing-a-server.md).

## <a name="see-also"></a>Viz také

[Nabídky a prostředky (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Aktivace](../mfc/activation-cpp.md)<br/>
[Servery](../mfc/servers.md)<br/>
[Containers](../mfc/containers.md)

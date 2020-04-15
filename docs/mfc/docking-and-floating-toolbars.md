---
title: Ukotvitelné a plovoucí panely nástrojů
ms.date: 11/04/2016
f1_keywords:
- CBRS_SIZE_DYNAMIC
- CBRS_SIZE_FIXED
helpviewer_keywords:
- size [MFC], toolbars
- size
- frame windows [MFC], toolbar docking
- CBRS_ALIGN_ANY constant [MFC]
- palettes, floating
- toolbars [MFC], docking
- CBRS_SIZE_DYNAMIC constant [MFC]
- floating toolbars
- toolbars [MFC], size
- toolbars [MFC], floating
- fixed-size toolbars
- CBRS_SIZE_FIXED constant [MFC]
- toolbar controls [MFC], wrapping
- toolbars [MFC], wrapping
- floating palettes
ms.assetid: b7f9f9d4-f629-47d2-a3c4-2b33fa6b51e4
ms.openlocfilehash: 30113565167b96b0df84a65768a1dfabe92ceffe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369775"
---
# <a name="docking-and-floating-toolbars"></a>Ukotvitelné a plovoucí panely nástrojů

Knihovna tříd Microsoft Foundation podporuje ukotvené panely nástrojů. Ukotvený panel nástrojů lze připojit nebo ukotvit k libovolné straně nadřazeného okna nebo jej lze odpojit nebo plovoucí ve vlastním okně minirámečku. Tento článek vysvětluje, jak používat ukotvené panely nástrojů ve vašich aplikacích.

Pokud použijete Průvodce aplikací ke generování kostry aplikace, budete vyzváni k výběru, zda chcete ukotvitelné panely nástrojů. Ve výchozím nastavení Průvodce aplikací generuje kód, který provádí tři akce potřebné k umístění dokovatelného panelu nástrojů v aplikaci:

- [Povolte ukotvení v okně rámce](#_core_enabling_docking_in_a_frame_window).

- [Povolte ukotvení panelu nástrojů](#_core_enabling_docking_for_a_toolbar).

- [Ukotvit panel nástrojů (do okna rámce).](#_core_docking_the_toolbar)

Pokud některý z těchto kroků chybí, aplikace zobrazí standardní panel nástrojů. Poslední dva kroky musí být provedeny pro každý ukotvený panel nástrojů v aplikaci.

Mezi další témata uvedená v tomto článku patří:

- [Plovoucí panel nástrojů](#_core_floating_the_toolbar)

- [Dynamická změna velikosti panelu nástrojů](#_core_dynamically_resizing_the_toolbar)

- [Nastavení obtékacích pozic pro panel nástrojů s pevným stylem](#_core_setting_wrap_positions_for_a_fixed_style_toolbar)

Viz ukázka obecné knihovny MFC [DOCKTOOL.](../overview/visual-cpp-samples.md)

## <a name="enabling-docking-in-a-frame-window"></a><a name="_core_enabling_docking_in_a_frame_window"></a>Povolení ukotvení v okně rámce

Chcete-li ukotvit panely nástrojů do okna rámce, musí být okno rámce (nebo cíl) povoleno, aby bylo možné dokovací systém. To se provádí pomocí [CFrameWnd::EnableDocking](../mfc/reference/cframewnd-class.md#enabledocking) funkce, která trvá jeden parametr *DWORD,* který je sada bitů stylu označující, která strana okna rámce přijímá ukotvení. Pokud se panel nástrojů chystá ukotvit a existuje více stran, do kterých by mohl `EnableDocking` být ukotven, strany uvedené v parametru předaných se používají v následujícím pořadí: nahoře, dole, vlevo, vpravo. Pokud chcete mít možnost ukotvit ovládací **CBRS_ALIGN_ANY** panely `EnableDocking`kdekoli, přejděte CBRS_ALIGN_ANY do .

## <a name="enabling-docking-for-a-toolbar"></a><a name="_core_enabling_docking_for_a_toolbar"></a>Povolení ukotvení pro panel nástrojů

Po přípravě cíle pro ukotvení je nutné připravit panel nástrojů (nebo zdroj) podobným způsobem. Volání [CControlBar::EnableDocking](../mfc/reference/ccontrolbar-class.md#enabledocking) pro každý panel nástrojů, který chcete ukotvit, určující cílové strany, ke kterým má být panel nástrojů ukotven. Pokud žádná ze stran zadaná ve výzvě `CControlBar::EnableDocking` neodpovídá stranám povoleným pro ukotvení v okně rámce, panel nástrojů nemůže ukotvit – bude plovoucí. Jakmile byl plovoucí, zůstane plovoucí panel nástrojů, nelze ukotvit do okna rámce.

Pokud je požadovaný efekt trvale plovoucí panel `EnableDocking` nástrojů, volání s parametrem 0. Potom zavolejte [CFrameWnd::FloatControlBar](../mfc/reference/cframewnd-class.md#floatcontrolbar). Panel nástrojů zůstává plovoucí, trvale nelze ukotvit kdekoli.

## <a name="docking-the-toolbar"></a><a name="_core_docking_the_toolbar"></a>Ukotvení panelu nástrojů

Rozhraní framework volá [CFrameWnd::DockControlBar,](../mfc/reference/cframewnd-class.md#dockcontrolbar) když se uživatel pokusí přetáhnout panel nástrojů na straně okna rámce, který umožňuje ukotvení.

Kromě toho můžete tuto funkci kdykoli volat, chcete-li řídicí panely ukotvit do okna rámce. To se obvykle provádí během inicializace. Více než jeden panel nástrojů lze ukotvit na určitou stranu okna rámce.

## <a name="floating-the-toolbar"></a><a name="_core_floating_the_toolbar"></a>Plovoucí panel nástrojů

Odpojení ukotveného panelu nástrojů od okna rámce se nazývá plovoucí panel nástrojů. Volání [CFrameWnd::FloatControlBar](../mfc/reference/cframewnd-class.md#floatcontrolbar) to provést. Určete pruh nástrojů, který má být plovoucí, bod, kam má být umístěn, a styl trasy, který určuje, zda je plovoucí panel nástrojů vodorovný nebo svislý.

Rozhraní Framework volá tuto funkci, když uživatel přetáhne panel nástrojů mimo své ukotvené umístění a klesne v umístění, kde není povoleno ukotvení. To může být kdekoli uvnitř nebo vně okna rámce. Stejně `DockControlBar`jako u , můžete také volat tuto funkci během inicializace.

MFC implementace dokovatelných panelů nástrojů neposkytuje některé rozšířené funkce nalezené v některých aplikacích, které podporují ukotvené panely nástrojů. Funkce, jako jsou přizpůsobitelné panely nástrojů, nejsou k dispozici.

## <a name="dynamically-resizing-the-toolbar"></a><a name="_core_dynamically_resizing_the_toolbar"></a>Dynamická změna velikosti panelu nástrojů

Od visual c++ verze 4.0 můžete uživatelům aplikace usnadnit dynamickou velikost plovoucích panelů nástrojů. Panel nástrojů má obvykle dlouhý, lineární tvar zobrazený vodorovně. Můžete však změnit orientaci panelu nástrojů a jeho tvar. Pokud například uživatel ukotví panel nástrojů proti jedné ze svislých stran okna rámečku, obrazec se změní na svislé rozložení. Je také možné změnit tvar panelu nástrojů do obdélníku s více řádky tlačítek.

Můžete:

- Určete dynamické velikosti jako charakteristiku panelu nástrojů.

- Určete pevné velikosti jako charakteristiku panelu nástrojů.

Chcete-li poskytnout tuto podporu, existují dva nové styly panelu nástrojů pro použití ve vašich [voláních CToolBar::Create](../mfc/reference/ctoolbar-class.md#create) členské funkce. Jsou to tyto:

- **CBRS_SIZE_DYNAMIC** Ovládací panel je dynamický.

- **CBRS_SIZE_FIXED** Ovládací panel je pevný.

Dynamický styl velikosti umožňuje uživateli změnit velikost panelu nástrojů, když je plovoucí, ale ne když je ukotven. Panel nástrojů "obtéká" tam, kde je potřeba změnit tvar, když uživatel přetáhne jeho okraje.

Velikost pevné styl zachovává obtékání stavy panelu nástrojů, kterým se stanoví umístění tlačítek v každém sloupci. Uživatel aplikace nemůže změnit tvar panelu nástrojů. Panel nástrojů se zalomí na určených místech, například umístění oddělovačů mezi tlačítky. Tento obrazec zachová bez ohledu na to, zda je panel nástrojů ukotven ý plovoucí. Efekt je pevná paleta s více sloupci tlačítek.

Můžete také použít [CToolBar::GetButtonStyle](../mfc/reference/ctoolbar-class.md#getbuttonstyle) vrátit stav a styl pro tlačítka na panelech nástrojů. Styl tlačítka určuje, jak se tlačítko zobrazí a jak reaguje na vstup uživatele; stav určuje, zda je tlačítko v zabaleném stavu.

## <a name="setting-wrap-positions-for-a-fixed-style-toolbar"></a><a name="_core_setting_wrap_positions_for_a_fixed_style_toolbar"></a>Nastavení obtékacích pozic pro panel nástrojů s pevným stylem

Pro panel nástrojů s pevnou velikostí stylu určete indexy tlačítek panelu nástrojů, ve kterých se panel nástrojů zalomí. Následující kód ukazuje, jak to provést v `OnCreate` přepsání hlavního okna rámce:

[!code-cpp[NVC_MFCDocViewSDI#10](../mfc/codesnippet/cpp/docking-and-floating-toolbars_1.cpp)]

Ukázka knihovny MFC General [DOCKTOOL](../overview/visual-cpp-samples.md) ukazuje, jak používat členské funkce tříd [CControlBar](../mfc/reference/ccontrolbar-class.md) a [CToolBar](../mfc/reference/ctoolbar-class.md) ke správě dynamického rozložení panelu nástrojů. Podívejte se na soubor EDITBAR. CPP v DOCKTOOL.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o

- [Základy panelu nástrojů](../mfc/toolbar-fundamentals.md)

- [Tipy nástrojů panelu nástrojů](../mfc/toolbar-tool-tips.md)

- [Používání starých panelů nástrojů](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>Viz také

[Implementace panelu nástrojů v prostředí MFC](../mfc/mfc-toolbar-implementation.md)

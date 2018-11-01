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
ms.openlocfilehash: 5688af1aa20589b88e2baa2f764c65fe7a417631
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599274"
---
# <a name="docking-and-floating-toolbars"></a>Ukotvitelné a plovoucí panely nástrojů

Knihovny Microsoft Foundation Class podporuje ukotvitelné panely nástrojů. Ukotvit panel nástrojů připojené, nebo ukotven na žádné straně nezašle nadřazenému oknu, nebo může být odpojeno, nebo obtékané v samostatném okně okna s minirámcem. Tento článek vysvětluje, jak použít ukotvitelné panely nástrojů ve svých aplikacích.

Pokud používáte Průvodce aplikací ke generování kostra aplikace, budete vyzváni k výběru, jestli chcete ukotvit panely nástrojů. Ve výchozím nastavení Průvodce aplikací generuje kód, který provádí tři akce, aby ukotvit panel nástrojů v aplikaci:

- [Povolit ukotvení v okně s rámečkem](#_core_enabling_docking_in_a_frame_window).

- [Povolit ukotvení pro panel nástrojů](#_core_enabling_docking_for_a_toolbar).

- [Ukotvení panelu nástrojů (do okna rámce)](#_core_docking_the_toolbar).

Pokud chybí některé z těchto kroků, vaše aplikace se zobrazí standardním panelu nástrojů. Poslední dva kroky musíte provést pro každý ukotvit panel nástrojů v aplikaci.

Další témata popsaná v tomto článku zahrnují:

- [Číslo s plovoucí čárkou panelu nástrojů](#_core_floating_the_toolbar)

- [Dynamicky změnu velikosti panelu nástrojů](#_core_dynamically_resizing_the_toolbar)

- [Nastavení obtékání pozice pro panel nástrojů-style](#_core_setting_wrap_positions_for_a_fixed_style_toolbar)

Najdete v ukázce MFC Obecné [DOCKTOOL](../visual-cpp-samples.md) příklady.

##  <a name="_core_enabling_docking_in_a_frame_window"></a> Povolení ukotvení v okně s rámečkem

Chcete-li ukotvit okno rámce panely nástrojů, okno rámce (nebo cílové) musí lze povolit ukotvení. To se provádí pomocí [CFrameWnd::EnableDocking](../mfc/reference/cframewnd-class.md#enabledocking) funkce, která přijímá jeden *DWORD* parametr, který představuje sadu styl bity určující, které straně okna rámce přijímá ukotvení. Pokud panel nástrojů je ukotvit a existuje více stran, které by mohly být ukotveno, strany uvedené v parametru předána `EnableDocking` se používají v tomto pořadí: horní, dolní, levý, pravý. Pokud chcete mít možnost ukotvení ovládací panely kdekoli, předejte **CBRS_ALIGN_ANY** k `EnableDocking`.

##  <a name="_core_enabling_docking_for_a_toolbar"></a> Povolení ukotvení pro panel nástrojů

Jakmile dokončíte přípravu cíle ukotvení, musíte připravit nástrojů (nebo zdroje) podobným způsobem. Volání [CControlBar::EnableDocking](../mfc/reference/ccontrolbar-class.md#enabledocking) pro každý panel nástrojů, které chcete ukotvit, určení cíle strany, který by měl ukotvení panelu nástrojů. Pokud žádný ze strany zadanou ve volání do `CControlBar::EnableDocking` odpovídat stran povoleno pro ukotvení v okně rámce, nelze ukotvení panelu nástrojů – bude float. Jakmile byl obtékané, zůstane na plovoucí panel nástrojů, nelze ukotvit okno rámce.

Pokud chcete efekt je trvale plovoucího panelu nástrojů, zavolejte `EnableDocking` s parametrem 0. Poté zavolejte [CFrameWnd::FloatControlBar](../mfc/reference/cframewnd-class.md#floatcontrolbar). Panel nástrojů zůstává s plovoucí desetinnou čárkou, trvale nelze ukotvit kdekoli.

##  <a name="_core_docking_the_toolbar"></a> Ukotvení panelu nástrojů

Rámec volá [CFrameWnd::DockControlBar](../mfc/reference/cframewnd-class.md#dockcontrolbar) když se uživatel pokusí o vyřadit na straně okna rámce, který umožňuje ukotvení panelu nástrojů.

Kromě toho můžete voláním této funkce v každém okamžiku ukotvení ovládacích panelů do okna rámce. To se obvykle provádí během inicializace. Více než jednoho panelu nástrojů můžete ukotven k okraji okna rámce.

##  <a name="_core_floating_the_toolbar"></a> Číslo s plovoucí čárkou panelu nástrojů

Odpojení ukotvit panel nástrojů okno rámce je volána s plovoucí desetinnou čárkou panelu nástrojů. Volání [CFrameWnd::FloatControlBar](../mfc/reference/cframewnd-class.md#floatcontrolbar) provedete to tak. Zadejte panelu nástrojů můžete být ponechán v neurčitém stavu, bod, ve kterém se má umístit a zarovnání styl, který určuje, zda plovoucí panel je vodorovný nebo svislý.

Rozhraní volá tuto funkci, když uživatel přetáhne vypnout místa ukotvení panelu nástrojů a sníží na místě, kde není povoleno ukotvení. To může být kdekoli uvnitř nebo vně okno rámce. Stejně jako u `DockControlBar`, můžete také voláním této funkce při inicializaci.

Implementace MFC ukotvitelné panelů nástrojů neposkytuje některé rozšířené funkce najít v některých aplikacích, které podporují ukotvitelné panely nástrojů. Nejsou k dispozici funkce, jako jsou přizpůsobitelné panely nástrojů.

##  <a name="_core_dynamically_resizing_the_toolbar"></a> Dynamicky změnu velikosti panelu nástrojů

Od verze Visual C++ verze 4.0 můžete si je možné pro uživatele vaší aplikace pro změnit dynamicky velikost plovoucí panely nástrojů. Panel nástrojů má obvykle, long, lineární tvaru zobrazovat vodorovně. Ale můžete změnit orientaci panelu nástrojů a jeho tvar. Například když uživatel ukotvené nástrojů pro jeden svislý okraji okna rámce, tvar se změní na svislé rozložení. Je také možné změnit tvar panelu nástrojů do obdélníku s více řádky tlačítek.

Můžeš:

- Zadejte dynamické úpravy velikosti jako vlastnost nástrojů.

- Zadejte nastavení pevné velikosti jako vlastnost nástrojů.

Chcete-li tuto funkci podporují, jsou dvě nové toolbar – styly pro použití ve voláních vašeho [CToolBar::Create](../mfc/reference/ctoolbar-class.md#create) členskou funkci. Možnosti jsou následující:

- **CBRS_SIZE_DYNAMIC** panel ovládacího prvku je dynamická.

- **CBRS_SIZE_FIXED** ovládací panel vyřešen.

Styl dynamická velikost umožňuje uživateli změnit velikost panelu nástrojů, zatímco je plovoucí, ale ne ukotven. Panelu nástrojů "zabalí" kde je potřeba změnit tvar, protože uživatel přetáhne jeho okrajů.

Velikost pevné styl zachová wrap stavy panelu nástrojů, stanovení polohy tlačítek v jednotlivých sloupcích. Vaše aplikace uživatel nemůže změnit tvar panelu nástrojů. Zabalí panelu nástrojů na určené místech, jako je například umístění oddělovače mezi tlačítky. Udržuje tohoto obrazce, zda je ukotvené nebo plovoucí panel nástrojů. Efekt je dlouhodobý palety s více sloupci tlačítek.

Můžete také použít [CToolBar::GetButtonStyle](../mfc/reference/ctoolbar-class.md#getbuttonstyle) vrátí stav a styl tlačítka na panely nástrojů. Určuje styl tohoto tlačítka vzhled tlačítka a jak reagovat na vstup uživatele; Stav určuje, zda tlačítko je ve stavu, zabalené.

##  <a name="_core_setting_wrap_positions_for_a_fixed_style_toolbar"></a> Nastavení obtékání pozice pro panel nástrojů-Style

Panel nástrojů s velikostí oprava styl určete panelu nástrojů tlačítko indexy, za které budou zahrnovat panelu nástrojů. Následující kód ukazuje, jak to provést v okna hlavního rámce `OnCreate` přepsat:

[!code-cpp[NVC_MFCDocViewSDI#10](../mfc/codesnippet/cpp/docking-and-floating-toolbars_1.cpp)]

Ukázky knihovny MFC Obecné [DOCKTOOL](../visual-cpp-samples.md) ukazuje, jak můžete členské funkce tříd [ccontrolbar –](../mfc/reference/ccontrolbar-class.md) a [ctoolbar –](../mfc/reference/ctoolbar-class.md) ke správě dynamických rozložení panelu nástrojů. Naleznete v souboru EDITBAR. CPP v DOCKTOOL.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Principy panelů nástrojů](../mfc/toolbar-fundamentals.md)

- [Popisy tlačítek na panelu nástrojů](../mfc/toolbar-tool-tips.md)

- [Použití starých panelů nástrojů](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>Viz také

[Implementace panelu nástrojů v prostředí MFC](../mfc/mfc-toolbar-implementation.md)


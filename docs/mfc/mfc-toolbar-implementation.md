---
title: Implementace panelu nástrojů v prostředí MFC
ms.date: 11/04/2016
helpviewer_keywords:
- toolbars [MFC], creating
- buttons [MFC], MFC toolbars
- toolbars [MFC], docking
- CToolBar class [MFC], creating toolbars
- MFC toolbars
- floating toolbars [MFC]
- toolbars [MFC], floating
- docking toolbars [MFC]
- bitmaps [MFC], toolbar
- toolbar controls [MFC]
- CToolBarCtrl class [MFC], implementing toolbars
- tool tips [MFC], enabling
- toolbars [MFC]
- toolbars [MFC], implementing MFC toolbars
ms.assetid: af3319ad-c430-4f90-8361-e6a2c06fd084
ms.openlocfilehash: 38811be765d4427c4083b8f142b54fb67b9076a0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359319"
---
# <a name="mfc-toolbar-implementation"></a>Implementace panelu nástrojů v prostředí MFC

Panel nástrojů je [ovládací panel,](../mfc/control-bars.md) který obsahuje bitmapové obrazy ovládacích prvků. Tyto obrázky se mohou chovat jako tlačítka, zaškrtávací políčka nebo přepínací tlačítka. Knihovna MFC dodává třídu [CToolbar](../mfc/reference/ctoolbar-class.md) pro správu panelů nástrojů.

Pokud jej povolíte, uživatelé panelů nástrojů knihovny MFC je mohou ukotvit k okraji okna nebo je "float" kdekoli v okně aplikace. Knihovna MFC nepodporuje přizpůsobitelné panely nástrojů, jako jsou panely ve vývojovém prostředí.

Knihovna MFC také podporuje tipy nástrojů: malá automaticky otevíraná okna, která popisují účel tlačítka panelu nástrojů, když umístíte ukazatel myši na tlačítko. Ve výchozím nastavení se při stisknutí tlačítka panelu nástrojů zobrazí na stavovém řádku stavový řetězec (pokud existuje). Můžete aktivovat aktualizaci stavového řádku "fly by" a zobrazit stavový řetězec, když je myš umístěna nad tlačítkem bez jeho stisknutí.

> [!NOTE]
> Od knihovny MFC verze 4.0 jsou panely nástrojů a tipy nástrojů implementovány pomocí systému Windows 95 a novějších funkcí namísto předchozí implementace specifické pro knihovnu MFC.

Z důvodu zpětné kompatibility si knihovna MFC zachová starší implementaci panelu nástrojů ve třídě `COldToolBar`. Dokumentace pro dřívější verze knihovny `COldToolBar` `CToolBar`MFC je popsána v části .

Vytvořte první panel nástrojů v programu výběrem možnosti Panel uprostřed aplikace. Můžete také vytvořit další panely nástrojů.

V tomto článku jsou uvedeny následující:

- [Tlačítka panelu nástrojů](#_core_toolbar_buttons)

- [Dokovací a plovoucí panely nástrojů](#_core_docking_and_floating_toolbars)

- [Panely nástrojů a tipy nástrojů](#_core_toolbars_and_tool_tips)

- [Třídy CToolBar a CToolBarCtrl](#_core_the_ctoolbar_and_ctoolbarctrl_classes)

- [Rastrový obrázek panelu nástrojů](#_core_the_toolbar_bitmap)

## <a name="toolbar-buttons"></a><a name="_core_toolbar_buttons"></a>Tlačítka panelu nástrojů

Tlačítka v panelu nástrojů jsou obdobná položkám v nabídce. Oba druhy objektů uživatelského rozhraní generují příkazy, které program zpracovává poskytnutím funkcí obslužné rutiny. Tlačítka panelu nástrojů často duplikují funkce příkazů nabídky a poskytují alternativní uživatelské rozhraní ke stejným funkcím. Taková duplikace je uspořádána jednoduše tím, že tlačítko a položka menu stejné ID.

Tlačítka na panelu nástrojů můžete zobrazit a chovat se jako tlačítka, zaškrtávací políčka nebo přepínací tlačítka. Další informace naleznete v tématu [ctoolbar](../mfc/reference/ctoolbar-class.md).

## <a name="docking-and-floating-toolbars"></a><a name="_core_docking_and_floating_toolbars"></a>Dokovací a plovoucí panely nástrojů

Panel nástrojů knihovny MFC může:

- Zůstaňte nehybní podél jedné strany nadřazeného okna.

- Uživatelem přetáhněte a "ukotvit" nebo připojit na libovolnou stranu nebo strany nadřazeného okna, které zadáte.

- Být "plovoucí", nebo odpojen od okna rámce, ve svém vlastním mini-rám okna, takže uživatel může pohybovat do libovolné vhodné polohy.

- Při plovoucím se velikosti.

Další informace naleznete v článku [Ukotvení a plovoucí panely nástrojů](../mfc/docking-and-floating-toolbars.md).

## <a name="toolbars-and-tool-tips"></a><a name="_core_toolbars_and_tool_tips"></a>Panely nástrojů a tipy nástrojů

MFC panely nástrojů mohou být také pro zobrazení "tipy nástrojů" - malé vyskakovací okna obsahující krátký textový popis účelu tlačítka panelu nástrojů. Když uživatel přesune ukazatel myši na tlačítko panelu nástrojů, objeví se okno s tipem nástroje, které nabízí nápovědu. Další informace naleznete v článku [Tipy nástrojů panelu nástrojů](../mfc/toolbar-tool-tips.md).

## <a name="the-ctoolbar-and-ctoolbarctrl-classes"></a><a name="_core_the_ctoolbar_and_ctoolbarctrl_classes"></a>Třídy CToolBar a CToolBarCtrl

Panely nástrojů aplikace spravujete prostřednictvím třídy [CToolBar](../mfc/reference/ctoolbar-class.md). Od knihovny MFC verze `CToolBar` 4.0 bylo znovu implementováno použití společného ovládacího prvku panelu nástrojů dostupného v systému Windows 95 nebo novějším a systému Windows NT verze 3.51 nebo novějším.

Výsledkem této reimplementace je méně kódu knihovny MFC pro panely nástrojů, protože knihovna MFC využívá podporu operačního systému. Reimplementace také zlepšuje schopnosti. Členské funkce `CToolBar` můžete použít k manipulaci s panely nástrojů nebo můžete získat odkaz na základní objekt [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) a volat jeho členské funkce pro přizpůsobení panelu nástrojů a další funkce.

> [!TIP]
> Pokud jste investovali hodně do starší implementace `CToolBar`knihovny MFC , tato podpora je stále k dispozici. Podívejte se na článek [Používání starých panelů nástrojů](../mfc/using-your-old-toolbars.md).

Viz také vzorek MFC General [DOCKTOOL](../overview/visual-cpp-samples.md).

## <a name="the-toolbar-bitmap"></a><a name="_core_the_toolbar_bitmap"></a>Bitová mapa panelu nástrojů

Jakmile je `CToolBar` objekt vytvořen, vytvoří obraz panelu nástrojů načtením jedné bitmapy, která obsahuje jeden obraz pro každé tlačítko. Průvodce aplikací vytvoří standardní bitmapu panelu nástrojů, kterou lze přizpůsobit pomocí [editoru panelu nástrojů](../windows/toolbar-editor.md)Visual C++ .

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o

- [Základy panelu nástrojů](../mfc/toolbar-fundamentals.md)

- [Dokovací a plovoucí panely nástrojů](../mfc/docking-and-floating-toolbars.md)

- [Tipy nástrojů panelu nástrojů](../mfc/toolbar-tool-tips.md)

- [Práce s ovládacím prvkem panel nástrojů](../mfc/working-with-the-toolbar-control.md)

- [Použití starých panelů nástrojů](../mfc/using-your-old-toolbars.md)

- [Třídy CToolBar](../mfc/reference/ctoolbar-class.md) a [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)

## <a name="see-also"></a>Viz také

[Panely nástrojů](../mfc/toolbars.md)<br/>
[Editor panelu nástrojů](../windows/toolbar-editor.md)

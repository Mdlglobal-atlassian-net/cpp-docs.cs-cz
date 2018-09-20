---
title: Implementace panelu nástrojů v prostředí MFC | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a95b5460ee28894d087d1896cbbac03cfb509166
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391199"
---
# <a name="mfc-toolbar-implementation"></a>Implementace panelu nástrojů v prostředí MFC

Je panel nástrojů [ovládací panel](../mfc/control-bars.md) , který obsahuje bitmapové obrázky ovládacích prvků. Tyto Image se může chovat jako tlačítek, zaškrtněte políčka nebo přepínací tlačítka. Knihovna MFC poskytuje třídy [ctoolbar –](../mfc/reference/ctoolbar-class.md) ke správě panely nástrojů.

Pokud ho povolíte, uživatelé panelů nástrojů MFC lze ukotvit k okraji okna nebo "float" je kdekoli v okně aplikace. MFC nepodporuje přizpůsobitelné panely nástrojů, jako ty ve vývojovém prostředí.

Knihovna MFC také podporuje popisů tlačítek: malé automaticky otevíraná okna, které popisují účel tlačítko panelu nástrojů, když umístíte ukazatel myši nad tlačítkem. Ve výchozím nastavení když uživatel stiskne tlačítko panelu nástrojů, řetězec stavu se zobrazí ve stavovém řádku (pokud existuje). "Při psaní ve" stavového řádku aktualizace zobrazí řetězec stav, když ukazatel myši umístěn nad tlačítkem bez klávesy ho můžete aktivovat.

> [!NOTE]
>  Od verze knihovny MFC verze 4.0 panely nástrojů a popisy tlačítek jsou implementovány pomocí Windows 95 a novější funkce místo předchozích implementacích specifické pro knihovny MFC.

Z důvodu zpětné kompatibility knihovny MFC uchovává starší implementace panelu nástrojů v třídě `COldToolBar`. Popis v dokumentaci pro starší verze knihovny MFC `COldToolBar` pod `CToolBar`.

Vytvoření první nástrojů ve svém programu výběrem možnosti panelu nástrojů v Průvodci aplikací. Můžete také vytvořit další panely nástrojů.

Následující jsou popsané v tomto článku:

- [Tlačítka panelu nástrojů](#_core_toolbar_buttons)

- [Ukotvitelné a plovoucí panely nástrojů](#_core_docking_and_floating_toolbars)

- [Panely nástrojů a tipů nástrojů](#_core_toolbars_and_tool_tips)

- [Ctoolbar – a ctoolbarctrl – třídy](#_core_the_ctoolbar_and_ctoolbarctrl_classes)

- [Rastrový obrázek panelu nástrojů](#_core_the_toolbar_bitmap)

##  <a name="_core_toolbar_buttons"></a> Tlačítka panelu nástrojů

Tlačítka v panelu nástrojů jsou podobná položek v nabídce. Oba typy objektů uživatelského rozhraní Generovat příkazy, které váš program zpracovává tím, že poskytuje funkce obslužné rutiny. Často tlačítka na panelu nástrojů duplicitní funkce příkazy nabídek, poskytuje alternativní uživatelské rozhraní ke stejné funkce. Tato duplikace uspořádána jednoduše tak, že udělíte tlačítka a položka nabídky se stejným ID.

Můžete vytvořit tlačítka na panelu nástrojů a chovají se jako tlačítek, zaškrtněte políčka nebo přepínací tlačítka. Další informace najdete v tématu třídy [ctoolbar –](../mfc/reference/ctoolbar-class.md).

##  <a name="_core_docking_and_floating_toolbars"></a> Ukotvitelné a plovoucí panely nástrojů

Panel nástrojů knihovny MFC můžete:

- Zůstat na jedné straně nezašle nadřazenému oknu bez pohybu.

- Kvůli usnadnění použití vypsány a "ukotven" nebo připojené uživatelem na straně nebo stranách nadřazené okno, které zadáte.

- "Plovoucí" nebo odpojeno od okna rámce v samostatném okně okna s minirámcem, takže uživatel můžu pohybovat ji na všechny vhodné místo.

- Změnit velikost při s plovoucí desetinnou čárkou.

Další informace najdete v článku [ukotvení a plovoucí panely nástrojů](../mfc/docking-and-floating-toolbars.md).

##  <a name="_core_toolbars_and_tool_tips"></a> Panely nástrojů a tipů nástrojů

Panely nástrojů rozhraní MFC lze provést také k zobrazení "nástroj tipy" – malý zobrazována místní okna, který obsahuje krátký textový popis účelu tlačítko panelu nástrojů. Jak uživatel přesouvá ukazatel myši nad tlačítko panelu nástrojů, panel nástrojů tip otevře do nabídky Nápověda. Další informace najdete v článku [popisy tlačítek na panelu nástrojů](../mfc/toolbar-tool-tips.md).

##  <a name="_core_the_ctoolbar_and_ctoolbarctrl_classes"></a> Ctoolbar – a třídy atributu CToolBarCtrl

Správa panelů nástrojů vaší aplikace prostřednictvím třídy [ctoolbar –](../mfc/reference/ctoolbar-class.md). Od verze knihovny MFC verze 4.0 `CToolBar` byla reimplemented pro běžné ovládací prvek panelu nástrojů dostupných v části Windows 95 nebo novější a Windows NT verze 3.51, aktualizace nebo novější.

Tato patřící třídě výsledků v menším množstvím kódu knihovny MFC pro panely nástrojů, protože knihovny MFC je použití podporovaných operačních systémech. Patřící třídě také zlepšuje funkce. Můžete použít `CToolBar` můžete členské funkce pro manipulaci s panely nástrojů, nebo získat odkaz na základní [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) objektu a volat její členské funkce pro přizpůsobení panelu nástrojů a dalších funkcí.

> [!TIP]
>  Pokud budete mít výrazně investovali do starší implementace MFC `CToolBar`, že je stále dostupná podpora. Přečtěte si článek [pomocí Your starých panelů nástrojů](../mfc/using-your-old-toolbars.md).

Také najdete v ukázce MFC Obecné [DOCKTOOL](../visual-cpp-samples.md).

##  <a name="_core_the_toolbar_bitmap"></a> Rastrový obrázek panelu nástrojů

Jednou vytvořený `CToolBar` objekt vytvoří obrázek panelu nástrojů načtením jediné bitmapě, která obsahuje jednu image pro každé tlačítko. Průvodce aplikace vytvoří, kterou můžete přizpůsobit rastrový obrázek standardním panelu nástrojů s jazykem Visual C++ [panelu nástrojů editoru](../windows/toolbar-editor.md).

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Principy panelů nástrojů](../mfc/toolbar-fundamentals.md)

- [Ukotvitelné a plovoucí panely nástrojů](../mfc/docking-and-floating-toolbars.md)

- [Popisy tlačítek na panelu nástrojů](../mfc/toolbar-tool-tips.md)

- [Práce s ovládacím prvkem panel nástrojů](../mfc/working-with-the-toolbar-control.md)

- [Použití starých panelů nástrojů](../mfc/using-your-old-toolbars.md)

- [Ctoolbar –](../mfc/reference/ctoolbar-class.md) a [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) třídy

## <a name="see-also"></a>Viz také

[Panely nástrojů](../mfc/toolbars.md)<br/>
[Editor panelu nástrojů](../windows/toolbar-editor.md)


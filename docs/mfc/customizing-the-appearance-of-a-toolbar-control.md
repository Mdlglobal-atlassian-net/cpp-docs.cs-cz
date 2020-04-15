---
title: Přizpůsobení vzhledu ovládacího prvku panel nástrojů
ms.date: 11/04/2016
f1_keywords:
- TBSTYLE_
helpviewer_keywords:
- flat toolbars
- CToolBar class [MFC], styles
- transparent toolbars
- TBSTYLE_ styles [MFC]
- CToolBarCtrl class [MFC], object styles
- toolbar controls [MFC], style
ms.assetid: fd0a73db-7ad1-4fe4-889b-02c3980f49e8
ms.openlocfilehash: 9f4f9d90113d5074555d1b0cc411f854abc67fe5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377465"
---
# <a name="customizing-the-appearance-of-a-toolbar-control"></a>Přizpůsobení vzhledu ovládacího prvku panel nástrojů

Třída `CToolBarCtrl` poskytuje mnoho stylů, které ovlivňují vzhled (a občas i chování) objektu panelu nástrojů. Upravte objekt panelu `dwCtrlStyle` nástrojů nastavením `CToolBarCtrl::Create` `CToolBar::CreateEx`parametru členské funkce (nebo) při prvním vytvoření ovládacího prvku panelu nástrojů.

Následující styly ovlivňují "3D" aspekt tlačítek panelu nástrojů a umístění textu tlačítka:

- **TBSTYLE_FLAT** Vytvoří plochý panel nástrojů, kde je pruh nástrojů i tlačítka průhledná. Text tlačítka se zobrazí pod bitmapami tlačítek. Při použití tohoto stylu se tlačítko pod kurzorem automaticky zvýrazní.

- **TBSTYLE_TRANSPARENT** Vytvoří průhledný panel nástrojů. Na průhledném panelu nástrojů je panel nástrojů průhledný, ale tlačítka nikoli. Text tlačítka se zobrazí pod bitmapami tlačítek.

- **TBSTYLE_LIST** Umístí text tlačítka napravo od bitmap tlačítek.

> [!NOTE]
> Aby se zabránilo problémům s překreslením, měly by být před viditelným objektem panelu nástrojů nastaveny styly **TBSTYLE_FLAT** a **TBSTYLE_TRANSPARENT.**

Následující styly určují, zda panel nástrojů umožňuje uživateli změnit umístění jednotlivých tlačítek v objektu panelu nástrojů pomocí přetažení:

- **TBSTYLE_ALTDRAG** Umožňuje uživatelům změnit polohu tlačítka panelu nástrojů přetažením při podržení klávesy ALT. Pokud tento styl není zadán, musí uživatel při přetahování tlačítka podržet klávesu SHIFT.

    > [!NOTE]
    >  Chcete-li povolit přetahování tlačítek panelu nástrojů, musí být zadán styl **CCS_ADJUSTABLE.**

- **TBSTYLE_REGISTERDROP** Generuje **TBN_GETOBJECT** oznamovací zprávy k vyžádání cílových objektů přetažení, když ukazatel myši předává tlačítka panelu nástrojů.

Zbývající styly ovlivňují vizuální a nevizuální aspekty objektu panelu nástrojů:

- **TBSTYLE_WRAPABLE** Vytvoří panel nástrojů, který může mít více řádků tlačítek. Tlačítka panelu nástrojů mohou "zalomit" na další řádek, když se panel nástrojů stane příliš úzkým, aby zahrnoval všechna tlačítka na stejném řádku. K obtékání dochází na hranicích oddělení a mimo skupiny.

- **TBSTYLE_CUSTOMERASE** Generuje **NM_CUSTOMDRAW** oznámení, když zpracovává **WM_ERASEBKGND** zprávy.

- **TBSTYLE_TOOLTIPS** Vytvoří ovládací prvek špičky nástroje, který může aplikace použít k zobrazení popisného textu tlačítek na panelu nástrojů.

Úplný seznam stylů panelů nástrojů a rozšířených stylů naleznete v [tématu Ovládací prvek panelu nástrojů a Styly tlačítek](/windows/win32/Controls/toolbar-control-and-button-styles) a [Rozšířené styly panelu nástrojů](/windows/win32/Controls/toolbar-extended-styles) v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[Používání atributu CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

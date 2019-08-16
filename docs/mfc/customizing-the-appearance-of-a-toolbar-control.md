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
ms.openlocfilehash: 590f0dce6c50ee6d0ca30c4c68e21787563bd686
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508727"
---
# <a name="customizing-the-appearance-of-a-toolbar-control"></a>Přizpůsobení vzhledu ovládacího prvku panel nástrojů

Třída `CToolBarCtrl` poskytuje mnoho stylů ovlivňujících vzhled (a občas i chování) objektu Toolbar. Upravte objekt Toolbar nastavením `dwCtrlStyle` parametru `CToolBarCtrl::Create` členské funkce (nebo `CToolBar::CreateEx`), při prvním vytvoření ovládacího prvku ToolBar.

Následující styly mají vliv na prostor "3D" tlačítek panelu nástrojů a umístění textu tlačítka:

- **TBSTYLE_FLAT** Vytvoří plochý panel nástrojů, kde jsou transparentní panely nástrojů i tlačítka. Text tlačítka se zobrazí v části rastry tlačítek. Při použití tohoto stylu je automaticky zvýrazněno tlačítko pod kurzorem.

- **TBSTYLE_TRANSPARENT** Vytvoří transparentní panel nástrojů. V transparentním panelu nástrojů je panel nástrojů transparentní, ale tlačítka nejsou. Text tlačítka se zobrazí v části rastry tlačítek.

- **TBSTYLE_LIST** Umístí text tlačítka vpravo od rastrových obrázků tlačítek.

> [!NOTE]
>  Aby nedocházelo k potížím s překreslením, měly by být nastaveny styly **TBSTYLE_FLAT** a **TBSTYLE_TRANSPARENT** před tím, než je objekt Toolbar viditelný.

Následující styly určují, zda panel nástrojů umožní uživateli přemístit jednotlivá tlačítka v rámci objektu Toolbar pomocí přetažení:

- **TBSTYLE_ALTDRAG** Umožňuje uživatelům změnit polohu tlačítka panelu nástrojů přetažením při stisknutí klávesy ALT. Pokud tento styl není zadaný, musí uživatel při přetahování tlačítka držet klávesu SHIFT.

    > [!NOTE]
    >  Aby bylo možné přetahovat tlačítka panelu nástrojů, je nutné zadat styl **CCS_ADJUSTABLE** .

- **TBSTYLE_REGISTERDROP** Generuje zprávy s oznámením **TBN_GETOBJECT** k vyžádání objektů cíle přetažení, když ukazatel myši projde tlačítky na panelu nástrojů.

Zbývající styly ovlivňují vizuální a nevizuální aspekty objektu Toolbar:

- **TBSTYLE_WRAPABLE** Vytvoří panel nástrojů, který může mít více řádků tlačítek. Tlačítka panelu nástrojů lze zabalit na další řádek, pokud je panel nástrojů příliš úzký na to, aby obsahoval všechna tlačítka na stejném řádku. Obtékání probíhá na hranicích oddělení a Neseskupení.

- **TBSTYLE_CUSTOMERASE** Generuje zprávy s oznámením **NM_CUSTOMDRAW** při zpracování zpráv **WM_ERASEBKGND** .

- **TBSTYLE_TOOLTIPS** Vytvoří ovládací prvek popis tlačítka, který může aplikace použít k zobrazení popisného textu pro tlačítka na panelu nástrojů.

Úplný seznam stylů panelů nástrojů a rozšířených stylů najdete v tématu [ovládací prvky panelu nástrojů a styly tlačítek](/windows/win32/Controls/toolbar-control-and-button-styles) a [panely nástrojů rozšířené styly](/windows/win32/Controls/toolbar-extended-styles) v Windows SDK.

## <a name="see-also"></a>Viz také:

[Používání atributu CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

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
ms.openlocfilehash: 8a0db3299ebb54d226edc1434dedbc6a04eb9b00
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62241804"
---
# <a name="customizing-the-appearance-of-a-toolbar-control"></a>Přizpůsobení vzhledu ovládacího prvku panel nástrojů

Třída `CToolBarCtrl` poskytuje mnoho styly, které ovlivňují vzhled (a v některých případech chování) objektu panelu nástrojů. Upravit objekt nástrojů tak, že nastavíte `dwCtrlStyle` parametr `CToolBarCtrl::Create` (nebo `CToolBar::CreateEx`) členské funkce, když vytvoříte první ovládací prvek panelu nástrojů.

Tyto styly ovlivní "3D" aspektu tlačítka panelu nástrojů a umístění text tlačítka:

- **TBSTYLE_FLAT** vytvoří bez stromové struktury kde jsou transparentní panelu nástrojů a tlačítka panelu nástrojů. Text na tlačítku se zobrazí v části rastrové obrázky tlačítka. Při použití tohoto stylu je automaticky zvýrazní tlačítko pod kurzor.

- **TBSTYLE_TRANSPARENT** vytvoří transparentní panelu nástrojů. Na panelu nástrojů transparentní panelu nástrojů je transparentní, ale tlačítka nejsou. Text na tlačítku se zobrazí v části rastrové obrázky tlačítka.

- **TBSTYLE_LIST** míst tlačítko text doprava rastrové obrázky tlačítka.

> [!NOTE]
>  Aby se zabránilo problémům repaint **TBSTYLE_FLAT** a **TBSTYLE_TRANSPARENT** styly by měla být nastavena před panelu nástrojů je viditelný.

Následující styly určit, pokud panel nástrojů umožňuje uživateli chcete změnit umístění jednotlivých tlačítek v objektu nástrojů pomocí přetažení:

- **TBSTYLE_ALTDRAG** umožňuje uživatelům změnit pozici panelu nástrojů tlačítko přetažením při držení klávesy ALT. Pokud není zadán tento styl, uživatel musí podržte stisknutou klávesu SHIFT při přetažení tlačítko.

    > [!NOTE]
    >  **CCS_ADJUSTABLE** styl musí být zadán umožňuje přetáhnout tlačítka panelu nástrojů.

- **TBSTYLE_REGISTERDROP** generuje **TBN_GETOBJECT** oznamovací zprávy o vyřadit cílové objektů při umístění ukazatele myši přetahovaného tlačítka na panelu nástrojů.

Zbývající styly ovlivní visual nevizuální aspektů a objekt panelu nástrojů:

- **TBSTYLE_WRAPABLE** vytvoří panel nástrojů, který může mít více řádků tlačítek. Tlačítka panelu nástrojů můžete "zabalení" zalamovat při panelu stane příliš úzký, aby zahrnout všechna tlačítka na stejném řádku. Zabalení probíhá v oddělení a nongroup hranice.

- **TBSTYLE_CUSTOMERASE** generuje **NM_CUSTOMDRAW** oznamovací zprávy při zpracování **WM_ERASEBKGND** zprávy.

- **TBSTYLE_TOOLTIPS** vytvoří nástroj ovládacím prvkem popis tlačítka, které aplikace můžete použít k zobrazení popisný text pro tlačítka na panelu nástrojů.

Úplný seznam všech toolbar – styly a styly rozšířené, naleznete v tématu [ovládací prvek panelu nástrojů a styly](/windows/desktop/Controls/toolbar-control-and-button-styles) a [Toolbar – styly rozšířené](/windows/desktop/Controls/toolbar-extended-styles) v sadě Windows SDK.

## <a name="see-also"></a>Viz také:

[Používání atributu CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

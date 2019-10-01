---
title: Dialogová okna
ms.date: 11/04/2016
helpviewer_keywords:
- modeless dialog boxes [MFC], MFC dialog boxes
- MFC, dialog boxes
- modal dialog boxes [MFC], MFC dialog boxes
- CDialog class [MFC], MFC dialog boxes
- MFC dialog boxes
ms.assetid: e4feea1a-8360-4ccb-9b84-507f1ccd9ef3
ms.openlocfilehash: 18b4c4d1386716a0a3282b88d6fdf5a701abce08
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685788"
---
# <a name="dialog-boxes"></a>Dialogová okna

Aplikace pro Windows často komunikují s uživatelem prostřednictvím dialogových oken. Třída [CDialog](../mfc/reference/cdialog-class.md) poskytuje rozhraní pro správu dialogových oken, Editor C++ dialogových oken umožňuje snadno navrhovat dialogová okna a vytvářet jejich šablony dialogových šablon a průvodci kódem zjednodušují proces inicializace a ověření ovládací prvky v dialogovém okně a shromažďují hodnoty zadané uživatelem.

Dialogová okna obsahují ovládací prvky, včetně:

- Běžné ovládací prvky pro Windows, jako jsou například pole pro úpravy, pushbuttons, seznamy, pole se seznamem, stromové ovládací prvky, ovládací prvky seznamu a indikátory průběhu.

- Ovládací prvky ActiveX.

- Ovládací prvky vykreslené vlastníkem: ovládací prvky, které zodpovídáte za kreslení v dialogovém okně.

Většina dialogových oken je modální, což vyžaduje, aby uživatel zavřel dialogové okno před použitím jakékoli jiné části programu. Je ale možné vytvářet nemodální dialogová okna, která uživatelům umožňují pracovat s ostatními okny, když je dialogové okno otevřené. Knihovna MFC podporuje oba typy dialogových oken s třídou `CDialog`. Ovládací prvky jsou uspořádány a spravovány pomocí prostředku šablony dialogového okna vytvořeného pomocí [editoru dialogových oken](../windows/dialog-editor.md).

[Seznamy vlastností](../mfc/property-sheets-mfc.md), označované také jako dialogová okna karta, jsou dialogová okna, která obsahují "stránky" samostatných ovládacích prvků dialogového okna. Každá stránka má v horní části složku souborů "TAB". Kliknutím na kartu přiřadíte tuto stránku do popředí dialogového okna.

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace

- [Příklad: zobrazení dialogového okna pomocí příkazu nabídky](../mfc/example-displaying-a-dialog-box-via-a-menu-command.md)

- [Komponenty dialogového okna v rozhraní .NET Framework](../mfc/dialog-box-components-in-the-framework.md)

- [Modální a nemodální dialogová okna](../mfc/modal-and-modeless-dialog-boxes.md)

- [Seznamy vlastností a stránky vlastností](../mfc/property-sheets-and-property-pages-mfc.md) v dialogovém okně

- [Vytvoření prostředku dialogového okna](../mfc/creating-the-dialog-resource.md)

- [Vytvoření třídy dialogového okna pomocí průvodců kódem](../mfc/creating-a-dialog-class-with-code-wizards.md)

- [Práce s dialogovými okny v MFC](../mfc/life-cycle-of-a-dialog-box.md)

- [Výměna dat dialogových oken (DDX) a ověřování (DDV)](../mfc/dialog-data-exchange-and-validation.md)

- [Typově bezpečný přístup k ovládacím prvkům v dialogovém okně](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)

- [Mapování zpráv systému Windows na třídu](../mfc/mapping-windows-messages-to-your-class.md)

- [Běžně přepsané členské funkce](../mfc/commonly-overridden-member-functions.md)

- [Běžně přidávané členské funkce](../mfc/commonly-added-member-functions.md)

- [Společné třídy dialogových oken](../mfc/common-dialog-classes.md)

- [Dialogová okna v OLE](../mfc/dialog-boxes-in-ole.md)

- Vytvoření aplikace, jejíž uživatelské rozhraní je dialogové okno: Přečtěte si ukázkové programy [CMNCTRL1](../overview/visual-cpp-samples.md) nebo [CMNCTRL2](../overview/visual-cpp-samples.md) . Tato možnost je také k dispozici v Průvodci aplikací.

- [Ukázky](../mfc/dialog-sample-list.md)

## <a name="see-also"></a>Další informace najdete v tématech

[Prvky uživatelského rozhraní](../mfc/user-interface-elements-mfc.md)

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
ms.openlocfilehash: 32a8f8784459338131d4893f25d8798f8031b68b
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "58778491"
---
# <a name="dialog-boxes"></a>Dialogová okna

Aplikace pro Windows se často komunikují s uživateli prostřednictvím dialogových oknech. Třída [CDialog](../mfc/reference/cdialog-class.md) poskytuje rozhraní pro správu dialogová okna, dialogové okno editor jazyka Visual C++ usnadňuje návrh dialogová okna a vytvoření jejich prostředků šablony dialogového okna a průvodců kódem zjednodušit proces inicializace a ověřování ovládacích prvků v dialogovém okně a získávání hodnoty zadané uživatelem.

Dialogová okna obsahují ovládací prvky, včetně:

- Běžné ovládací prvky Windows, jako upravit pole, tlačítek, pole se seznamem, pole se seznamem, ovládacích prvků strom, ovládacích prvcích seznam a indikátory průběhu.

- Ovládací prvky ActiveX.

- Vykreslování ovládacích prvků: ovládací prvky, které vám jsou zodpovědné za vykreslování v dialogovém okně.

Většina dialogová okna jsou modální, což vyžaduje, aby uživatel před použitím jakékoliv jiné části programu zavřete dialogové okno. Ale je možné vytvořit nemodálních dialogových oken, které umožňují uživatelům pracovat s ostatními okny při otevřeném dialogovém okně. MFC podporuje oba typy dialogové okno s třídou `CDialog`. Ovládací prvky jsou uspořádány a spravují s použitím šablony dialogového okna prostředků, vytvořené pomocí [editoru dialogového okna](../windows/dialog-editor.md).

[Seznamy vlastností](../mfc/property-sheets-mfc.md), označované také jako kartu dialogová okna, jsou dialogová okna, které obsahují výraz "stránky" ovládacích prvků liší – dialogové okno. Každá stránka má složku souborů "kartu" v horní části. Kliknutím na kartu přináší tuto stránku do přední části dialogových oken.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Příklad: Zobrazení dialogového okna pomocí příkazu nabídky](../mfc/example-displaying-a-dialog-box-via-a-menu-command.md)

- [Komponenty dialogového okna v rozhraní framework](../mfc/dialog-box-components-in-the-framework.md)

- [Modální a nemodální dialogová okna](../mfc/modal-and-modeless-dialog-boxes.md)

- [Seznamy vlastností a stránky vlastností](../mfc/property-sheets-and-property-pages-mfc.md) v dialogovém okně

- [Vytvoření prostředku dialogového okna](../mfc/creating-the-dialog-resource.md)

- [Vytvoření třídy dialogového okna s použitím průvodců kódem](../mfc/creating-a-dialog-class-with-code-wizards.md)

- [Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)

- [Výměna dat dialogových oken (DDX) a ověřování (DDV)](../mfc/dialog-data-exchange-and-validation.md)

- [Typově bezpečný přístup k ovládacím prvkům v dialogovém okně](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)

- [Mapování zpráv Windows na třídu](../mfc/mapping-windows-messages-to-your-class.md)

- [Běžně přepisované členské funkce](../mfc/commonly-overridden-member-functions.md)

- [Běžně přidávané členské funkce](../mfc/commonly-added-member-functions.md)

- [Společné třídy dialogových oken](../mfc/common-dialog-classes.md)

- [Dialogová okna v prostředí OLE](../mfc/dialog-boxes-in-ole.md)

- Vytvoření aplikace, jejichž uživatelské rozhraní je dialogové okno: najdete v článku [CMNCTRL1](../overview/visual-cpp-samples.md) nebo [CMNCTRL2](../overview/visual-cpp-samples.md) ukázkové programy. Tuto možnost také poskytuje průvodce aplikací.

- [Ukázky](../mfc/dialog-sample-list.md)

## <a name="see-also"></a>Viz také:

[Prvky uživatelského rozhraní](../mfc/user-interface-elements-mfc.md)

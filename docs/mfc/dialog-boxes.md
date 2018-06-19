---
title: Dialogová okna | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- modeless dialog boxes [MFC], MFC dialog boxes
- MFC, dialog boxes
- modal dialog boxes [MFC], MFC dialog boxes
- CDialog class [MFC], MFC dialog boxes
- MFC dialog boxes
ms.assetid: e4feea1a-8360-4ccb-9b84-507f1ccd9ef3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2c8de283d81aa9d260b891f285f06555dc67895f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346672"
---
# <a name="dialog-boxes"></a>Dialogová okna
Aplikace pro Windows se často komunikují s uživateli pomocí dialogových oken. Třída [CDialog](../mfc/reference/cdialog-class.md) poskytuje rozhraní pro správu dialogová okna, dialogové okno editor Visual C++ usnadňuje návrh dialogových oken a vytvoření jejich prostředky šablony dialogového okna a průvodců kódem zjednodušit proces inicializace a ověřování ovládacích prvků v dialogovém okně a shromažďování hodnot zadaných uživatelem.  
  
 Dialogová okna obsahují ovládací prvky, včetně:  
  
-   Běžné ovládací prvky Windows, jako upravit polí, tlačítek, seznamy, pole se seznamem, ovládací prvky stromů, ovládací prvky seznamu a indikátory průběhu.  
  
-   Ovládací prvky ActiveX.  
  
-   Ovládací prvky vykreslované uživatelem: ovládací prvky, které jste zodpovědní za kreslení v dialogovém okně.  
  
 Většina dialogová okna jsou modální, které vyžadují, aby uživatel zavřete dialogové okno před použitím jiných součástí programu. Ale je možné vytvořit nemodální dialogová okna, které umožňují uživatelům pracovat s jinými při otevřené dialogové okno. Podporuje oba typy dialogové okno s třídou MFC `CDialog`. Ovládací prvky jsou uspořádány a spravují pomocí prostředku šablony dialogového okna, vytvořené pomocí [editoru dialogového okna](../windows/dialog-editor.md).  
  
 [Seznam vlastností](../mfc/property-sheets-mfc.md), také známé jako kartě dialogových oken, jsou dialogových oken, které obsahují "stránky" distinct dialogové ovládacích prvků. Každé stránce má souboru složku "kartu" v horní části. Kliknutím na kartě přenést této stránce do popředí dialogového okna.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Příklad: Zobrazení dialogového okna pomocí příkazu v nabídce](../mfc/example-displaying-a-dialog-box-via-a-menu-command.md)  
  
-   [Komponenty dialogového okna v rozhraní framework](../mfc/dialog-box-components-in-the-framework.md)  
  
-   [Modální a nemodální dialogová okna](../mfc/modal-and-modeless-dialog-boxes.md)  
  
-   [Seznam vlastností a stránky vlastností](../mfc/property-sheets-and-property-pages-mfc.md) v dialogovém okně  
  
-   [Vytvoření prostředku dialogového okna](../mfc/creating-the-dialog-resource.md)  
  
-   [Vytvoření třídy dialogového okna s použitím průvodců kódem](../mfc/creating-a-dialog-class-with-code-wizards.md)  
  
-   [Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)  
  
-   [Výměna dat dialogových oken (DDX) a ověřování (DDV)](../mfc/dialog-data-exchange-and-validation.md)  
  
-   [Typově bezpečný přístup k ovládacím prvkům v dialogovém okně](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)  
  
-   [Mapování zpráv systému Windows na třídu](../mfc/mapping-windows-messages-to-your-class.md)  
  
-   [Běžně přepisované členské funkce](../mfc/commonly-overridden-member-functions.md)  
  
-   [Běžně přidávané členské funkce](../mfc/commonly-added-member-functions.md)  
  
-   [Společné třídy dialogových oken](../mfc/common-dialog-classes.md)  
  
-   [Dialogová okna v prostředí OLE](../mfc/dialog-boxes-in-ole.md)  
  
-   Vytvoření aplikace, jejichž uživatelské rozhraní je dialogové okno: najdete v článku [CMNCTRL1](../visual-cpp-samples.md) nebo [CMNCTRL2](../visual-cpp-samples.md) ukázkové programy. Průvodce aplikací poskytuje také tuto možnost.  
  
-   [Ukázky](../mfc/dialog-sample-list.md)  
  
## <a name="see-also"></a>Viz také  
 [Prvky uživatelského rozhraní](../mfc/user-interface-elements-mfc.md)

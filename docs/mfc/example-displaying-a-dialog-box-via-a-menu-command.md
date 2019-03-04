---
title: 'Příklad: Zobrazení dialogového okna pomocí příkazu nabídky'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], examples
- MFC dialog boxes [MFC], displaying
- modeless dialog boxes [MFC], displaying
- dialog boxes [MFC], MFC
- modal dialog boxes [MFC], displaying
- examples [MFC], dialog boxes
- menu items [MFC], examples
ms.assetid: e8692549-acd7-478f-9c5e-ba310ce8cccd
ms.openlocfilehash: 8c60469747c24b4c295348a14cb569c4118c76d9
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57260475"
---
# <a name="example-displaying-a-dialog-box-via-a-menu-command"></a>Příklad: Zobrazení dialogového okna pomocí příkazu nabídky

Toto téma obsahuje postupy, které:

- Zobrazení modálního dialogového okna pomocí příkazu nabídky.

- Zobrazte dialogové okno nemodální prostřednictvím příkazu nabídky.

Oba postupy ukázky jsou pro aplikace MFC a budou fungovat v aplikaci, kterou vytvoříte pomocí [Průvodce aplikací knihovny MFC](../mfc/reference/mfc-application-wizard.md).

Postupy použijte následující názvy a hodnoty:

|Položka|Vlastnosti Name nebo value|
|----------|-------------------|
|Aplikace|DisplayDialog|
|Příkaz nabídky|Testovací příkaz v nabídce Zobrazit; ID příkazu = ID_VIEW_TEST|
|Dialogové okno|Dialogové okno testu; Třída = CTestDialog; Soubor hlaviček = TestDialog.h; Proměnná = testdlg ptestdlg|
|Obslužná rutina příkazu|OnViewTest|

### <a name="to-display-a-modal-dialog-box"></a>Chcete-li zobrazit modální dialogové okno

1. Vytvoření příkazu nabídky; Zobrazit [vytváření nabídek nebo nabídek](../windows/creating-a-menu.md).

1. Vytvořit dialogové okno. Zobrazit [spuštění editoru dialogových oken](../windows/creating-a-new-dialog-box.md).

1. Přidejte třídu pro vaše dialogové okno. Zobrazit [přidání třídy](../ide/adding-a-class-visual-cpp.md) Další informace.

1. V **zobrazení tříd**, vyberte třídu dokumentu (CDisplayDialogDoc). V **vlastnosti** okna, klikněte na tlačítko **události** tlačítko. ID příkazu nabídky (ID_VIEW_TEST) v levém podokně dvakrát klikněte **vlastnosti** okna a vyberte **příkaz**. V pravém podokně klikněte na šipku dolů a vyberte  **\<Přidat > OnViewTest**.

   Pokud jste přidali příkaz nabídky mainframových aplikace MDI, vyberte místo toho – třída aplikace (CDisplayDialogApp).

1. Přidejte následující include příkaz CDisplayDialogDoc.cpp (nebo CDisplayDialogApp.cpp) po existující #include:

   [!code-cpp[NVC_MFCControlLadenDialog#42](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_1.cpp)]

1. Přidejte následující kód, který `OnViewTest` implementovat funkci:

   [!code-cpp[NVC_MFCControlLadenDialog#43](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_2.cpp)]

### <a name="to-display-a-modeless-dialog-box"></a>Chcete-li zobrazit dialogové okno nemodální

1. Proveďte první čtyři kroky zobrazíte modální dialogové okno, s výjimkou třídy zobrazení (CDisplayDialogView) vyberte v kroku 4.

1. Upravte DisplayDialogView.h:

   - Deklarace pole třídy dialogového okna, předchozí deklaraci první třídy:

         [!code-cpp[NVC_MFCControlLadenDialog#44](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_3.h)]

   - Deklarujte ukazatel na dialogovém okně za veřejnou část atributy:

         [!code-cpp[NVC_MFCControlLadenDialog#45](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_4.h)]

1. Edit DisplayDialogView.cpp:

   - Přidejte že následující příkazu #include po existující #include:

         [!code-cpp[NVC_MFCControlLadenDialog#42](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_1.cpp)]

   - Přidejte následující kód do konstruktoru:

         [!code-cpp[NVC_MFCControlLadenDialog#46](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_5.cpp)]

   - Destruktor přidejte následující kód:

         [!code-cpp[NVC_MFCControlLadenDialog#47](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_6.cpp)]

   - Přidejte následující kód, který `OnViewTest` implementovat funkci:

         [!code-cpp[NVC_MFCControlLadenDialog#48](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_7.cpp)]

## <a name="see-also"></a>Viz také:

[Dialogová okna](../mfc/dialog-boxes.md)<br/>
[Modální a nemodální dialogová okna](../mfc/modal-and-modeless-dialog-boxes.md)

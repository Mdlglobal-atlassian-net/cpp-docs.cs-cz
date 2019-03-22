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
ms.openlocfilehash: 1e730125e47609f0bf87814b32962336cb752b04
ms.sourcegitcommit: c1f646c8b72f330fa8cf5ddb0f8f261ba10d16f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2019
ms.locfileid: "58328256"
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

   ```cpp
   #include "TestDialog.h"
   ```

1. Přidejte následující kód, který `OnViewTest` implementovat funkci:

   ```cpp
   CTestDialog testdlg;
   testdlg.DoModal();  
   ```

### <a name="to-display-a-modeless-dialog-box"></a>Chcete-li zobrazit dialogové okno nemodální

1. Proveďte první čtyři kroky zobrazíte modální dialogové okno, s výjimkou třídy zobrazení (CDisplayDialogView) vyberte v kroku 4.

1. Upravte DisplayDialogView.h:

   - Deklarace pole třídy dialogového okna, předchozí deklaraci první třídy:

   ```cpp
   class CTestDialog;
   ```

   - Deklarujte ukazatel na dialogovém okně za veřejnou část atributy:

   ```cpp
   CTestDialog* m_pTestDlg;
   ```

1. Edit DisplayDialogView.cpp:

   - Přidejte že následující příkazu #include po existující #include:

   ```cpp
   #include "TestDialog.h"
   ```

   - Přidejte následující kód do konstruktoru:

   ```cpp
   m_pTestDlg = NULL;
   ```

   - Destruktor přidejte následující kód:

   ```cpp
   delete m_pTestDlg;
   ```

   - Přidejte následující kód, který `OnViewTest` implementovat funkci:

   ```cpp
   if (NULL == m_pTestDlg)
   {
      m_pTestDlg = new CTestDialog(this);
      m_pTestDlg->Create(CTestDialog::IDD, this);
   }
   m_pTestDlg->ShowWindow(SW_SHOW); 
   ```

## <a name="see-also"></a>Viz také:

[Dialogová okna](../mfc/dialog-boxes.md)<br/>
[Modální a nemodální dialogová okna](../mfc/modal-and-modeless-dialog-boxes.md)

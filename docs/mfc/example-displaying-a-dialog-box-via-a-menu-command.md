---
title: 'Příklad: Zobrazení dialogového okna pomocí příkazu nabídky'
ms.date: 09/07/2019
helpviewer_keywords:
- MFC dialog boxes [MFC], examples
- MFC dialog boxes [MFC], displaying
- modeless dialog boxes [MFC], displaying
- dialog boxes [MFC], MFC
- modal dialog boxes [MFC], displaying
- examples [MFC], dialog boxes
- menu items [MFC], examples
ms.assetid: e8692549-acd7-478f-9c5e-ba310ce8cccd
ms.openlocfilehash: 12c919c1c79a3e40a1322f3f73398b90af2fad5f
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2019
ms.locfileid: "71095920"
---
# <a name="example-displaying-a-dialog-box-via-a-menu-command"></a>Příklad: Zobrazení dialogového okna pomocí příkazu nabídky

Toto téma obsahuje postupy:

- Zobrazí modální dialogové okno pomocí příkazu nabídky.

- Zobrazí nemodální dialogové okno pomocí příkazu nabídky.

Oba ukázkové postupy jsou pro aplikace MFC a budou fungovat v aplikaci, kterou vytvoříte pomocí [Průvodce aplikací knihovny MFC](../mfc/reference/mfc-application-wizard.md).

Postupy používají následující názvy a hodnoty:

|Položka|Název nebo hodnota|
|----------|-------------------|
|Aplikace|DisplayDialog|
|Příkaz nabídky|Test příkazu v nabídce zobrazení; ID příkazu = ID_VIEW_TEST|
|Dialogové okno|Dialogové okno test; Class = CTestDialog; Hlavičkový soubor = TestDialog. h; Proměnná = testdlg, ptestdlg|
|Obslužná rutina příkazu|OnViewTest|

### <a name="to-display-a-modal-dialog-box"></a>Zobrazení modálního dialogového okna

1. Vytvoření příkazu nabídky; viz [vytváření nabídek nebo položek nabídky](../windows/creating-a-menu.md).

1. Vytvoření dialogového okna; viz [spuštění editoru dialogového okna](../windows/creating-a-new-dialog-box.md).

1. Přidejte třídu pro dialogové okno. Další informace najdete v tématu věnovaném [Přidání třídy](../ide/adding-a-class-visual-cpp.md) .

1. V **zobrazení tříd**vyberte třídu dokumentu (CDisplayDialogDoc). V okně **vlastnosti** klikněte na tlačítko **události** . Dvakrát klikněte na ID příkazu nabídky (ID_VIEW_TEST). Potom klikněte na šipku dolů a vyberte  **\<přidat > OnViewTest**.

   Pokud jste přidali příkaz nabídky do sálového počítače aplikace MDI, vyberte místo toho třídu aplikace (CDisplayDialogApp).

1. Přidejte následující příkaz include do CDisplayDialogDoc. cpp (nebo CDisplayDialogApp. cpp) za existující příkazy include:

   ```cpp
   #include "TestDialog.h"
   ```

1. Přidejte následující kód k `OnViewTest` implementaci funkce:

   ```cpp
   CTestDialog testdlg;
   testdlg.DoModal(); 
   ```

### <a name="to-display-a-modeless-dialog-box"></a>Zobrazení nemodálního dialogového okna

1. Proveďte první čtyři kroky pro zobrazení modálního dialogového okna s výjimkou výběru třídy zobrazení (CDisplayDialogView) v kroku 4.

1. Upravit DisplayDialogView. h:

   - Deklarujte třídu dialogového okna před první deklarací třídy:

   ```cpp
   class CTestDialog;
   ```

   - Deklarovat ukazatel na dialogové okno po veřejné části atributů:

   ```cpp
   CTestDialog* m_pTestDlg;
   ```

1. Edit DisplayDialogView.cpp:

   - Přidejte následující příkaz include za existující příkazy include:

   ```cpp
   #include "TestDialog.h"
   ```

   - Do konstruktoru přidejte následující kód:

   ```cpp
   m_pTestDlg = NULL;
   ```

   - Do destruktoru přidejte následující kód:

   ```cpp
   delete m_pTestDlg;
   ```

   - Přidejte následující kód k `OnViewTest` implementaci funkce:

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

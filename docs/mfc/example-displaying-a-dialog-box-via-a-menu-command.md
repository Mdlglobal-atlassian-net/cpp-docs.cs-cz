---
title: 'Příklad: Zobrazení dialogového okna pomocí příkazu v nabídce | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], examples
- MFC dialog boxes [MFC], displaying
- modeless dialog boxes [MFC], displaying
- dialog boxes [MFC], MFC
- modal dialog boxes [MFC], displaying
- examples [MFC], dialog boxes
- menu items [MFC], examples
ms.assetid: e8692549-acd7-478f-9c5e-ba310ce8cccd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 20d355215388861a7bc2586c2c253cd551124809
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="example-displaying-a-dialog-box-via-a-menu-command"></a>Příklad: Zobrazení dialogového okna pomocí příkazu v nabídce
Toto téma obsahuje postup:  
  
-   Zobrazí modální dialogové okno prostřednictvím příkazu nabídky.  
  
-   Zobrazte dialogové okno nemodální prostřednictvím příkazu nabídky.  
  
 Ukázka procedury jsou pro aplikace MFC a bude fungovat v aplikaci vytvoříte pomocí [Průvodce aplikací knihovny MFC](../mfc/reference/mfc-application-wizard.md).  
  
 Postupy použijte následující názvy a hodnoty:  
  
|Položka|Název nebo hodnota|  
|----------|-------------------|  
|Aplikace|DisplayDialog|  
|Příkaz nabídky|Test příkazu v nabídce Zobrazit; ID příkazu = ID_VIEW_TEST|  
|Dialogové okno|Dialogové okno Test; Třída = CTestDialog; Soubor hlaviček = TestDialog.h; Proměnná = testdlg, ptestdlg|  
|Obslužná rutina příkazu|OnViewTest|  
  
### <a name="to-display-a-modal-dialog-box"></a>Chcete-li zobrazit modální dialogové okno  
  
1.  Vytvoření příkazu nabídky; v tématu [vytváření nabídek nebo položky nabídky](../windows/creating-a-menu.md).  
  
2.  Vytvořit dialogové okno. v tématu [spouštění editoru dialogových oken](../windows/creating-a-new-dialog-box.md).  
  
3.  Přidejte třídu pro váš dialogové okno. V tématu [přidání třídy](../ide/adding-a-class-visual-cpp.md) Další informace.  
  
4.  V **zobrazení tříd**, vyberte třídu dokumentu (CDisplayDialogDoc). V **vlastnosti** okně klikněte **události** tlačítko. ID příkazu nabídky (ID_VIEW_TEST) v levém podokně dvakrát klikněte **vlastnosti** a vyberte **příkaz**. V pravém podokně klikněte na šipku dolů a vyberte  **\<Přidat > OnViewTest**.  
  
     Pokud jste přidali příkaz nabídky k sálové aplikace MDI, vyberte třídu aplikace (CDisplayDialogApp).  
  
5.  Přidejte následující include příkaz CDisplayDialogDoc.cpp (nebo CDisplayDialogApp.cpp) po existující zahrnují příkazy:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#42](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_1.cpp)]  
  
6.  Přidejte následující kód, který `OnViewTest` implementovat funkce:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#43](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_2.cpp)]  
  
### <a name="to-display-a-modeless-dialog-box"></a>Chcete-li zobrazit dialogové okno nemodální  
  
1.  Proveďte první čtyři kroky, chcete-li zobrazit modální dialogové okno, s výjimkou vyberte třídy zobrazení (CDisplayDialogView) v kroku 4.  
  
2.  Upravte DisplayDialogView.h:  
  
    -   Deklarujte třídy dialogového okna předchází deklaraci první třídy:  
  
         [!code-cpp[NVC_MFCControlLadenDialog#44](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_3.h)]  
  
    -   Deklarujte ukazatel na dialogové okno po veřejné části atributy:  
  
         [!code-cpp[NVC_MFCControlLadenDialog#45](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_4.h)]  
  
3.  Upravte DisplayDialogView.cpp:  
  
    -   Přidáte že následující obsahovat příkaz po existující zahrnují příkazy:  
  
         [!code-cpp[NVC_MFCControlLadenDialog#42](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_1.cpp)]  
  
    -   Přidejte následující kód do konstruktoru:  
  
         [!code-cpp[NVC_MFCControlLadenDialog#46](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_5.cpp)]  
  
    -   Přidejte následující kód destruktoru:  
  
         [!code-cpp[NVC_MFCControlLadenDialog#47](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_6.cpp)]  
  
    -   Přidejte následující kód, který `OnViewTest` implementovat funkce:  
  
         [!code-cpp[NVC_MFCControlLadenDialog#48](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_7.cpp)]  
  
 Navíc najdete v následujícím článku znalostní báze Knowledge Base:  
  
-   Q251059: Postupy: Zadejte název vlastní okno třídy dialogového okna knihovny MFC  
  
## <a name="see-also"></a>Viz také  
 [Dialogová okna](../mfc/dialog-boxes.md)   
 [Modální a nemodální dialogová okna](../mfc/modal-and-modeless-dialog-boxes.md)


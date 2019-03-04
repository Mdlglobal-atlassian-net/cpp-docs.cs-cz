---
title: Společné třídy dialogových oken
ms.date: 11/04/2016
helpviewer_keywords:
- dialog classes [MFC]
- dialog boxes [MFC], Windows common dialogs
- common dialog boxes [MFC], common dialog classes
- common dialog classes [MFC]
- MFC dialog boxes [MFC], Windows common dialogs
- Windows common dialogs [MFC]
- dialog classes [MFC], common
- common dialog boxes [MFC]
ms.assetid: 5c4f6443-896c-4b05-a7df-8169fdadc71d
ms.openlocfilehash: 5efd885421d8c73c191e2a5603f37d1df85a5168
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57303063"
---
# <a name="common-dialog-classes"></a>Společné třídy dialogových oken

Kromě tříd [CDialog](../mfc/reference/cdialog-class.md), knihovna MFC poskytuje několik tříd odvozených z `CDialog` zapouzdřují běžně používané dialogových oknech, jak je znázorněno v následující tabulce. Dialogová okna zapouzdřené se nazývají "běžných dialogových oknech" a jsou součástí Windows běžné dialogového okna knihovny (COMMDLG. KNIHOVNY DLL). V dialogovém okně prostředky a kódu pro tyto třídy jsou k dispozici v Windows společná dialogová okna, které jsou součástí Windows verze 3.1 nebo novější.

### <a name="common-dialog-classes"></a>Společné třídy dialogových oken

|Třídy odvozené dialogového okna|Účel|
|--------------------------|-------------|
|[CColorDialog](../mfc/reference/ccolordialog-class.md)|Umožňuje výběr barev uživatelské.|
|[CFileDialog](../mfc/reference/cfiledialog-class.md)|Umožňuje uživateli vybrat název souboru, chcete-li otevřít nebo uložit.|
|[CFindReplaceDialog.](../mfc/reference/cfindreplacedialog-class.md)|Umožňuje uživatelům Zahájit hledání nebo nahradit operace do textového souboru.|
|[CFontDialog](../mfc/reference/cfontdialog-class.md)|Umožňuje uživatelům určit písmo.|
|[CPrintDialog](../mfc/reference/cprintdialog-class.md)|Umožňuje uživatelům zadat informace pro tiskové úlohy.|
|[CPrintDialogEx](../mfc/reference/cprintdialogex-class.md)|Seznamem vlastností tisku Windows.|

Další informace o společné třídy dialogových oken, zobrazit názvy jednotlivých tříd v *odkaz knihovny MFC*. Knihovna MFC poskytuje také řadu standardního dialogového okna třídy používané pro OLE. Informace o těchto tříd naleznete v tématu základní třídy, [coledialog –](../mfc/reference/coledialog-class.md)v *odkaz knihovny MFC*.

Tři třídy v knihovně MFC mají podobné dialogové okno Vlastnosti. Informace o třídách [CFormView](../mfc/reference/cformview-class.md), [CRecordView](../mfc/reference/crecordview-class.md), a [CDaoRecordView](../mfc/reference/cdaorecordview-class.md), naleznete v tématu třídy v *odkaz knihovny MFC*. Informace o třídě [CDialogBar](../mfc/reference/cdialogbar-class.md), naleznete v tématu [dialogové pruhy](../mfc/dialog-bars.md).

## <a name="see-also"></a>Viz také:

[Dialogová okna](../mfc/dialog-boxes.md)<br/>
[Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Dialogová okna v prostředí OLE](../mfc/dialog-boxes-in-ole.md)

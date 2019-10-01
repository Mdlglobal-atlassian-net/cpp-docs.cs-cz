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
ms.openlocfilehash: d11d0978763d9599b0471a8e994f15a267f7cb8f
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685562"
---
# <a name="common-dialog-classes"></a>Společné třídy dialogových oken

Kromě třídy [CDialog](../mfc/reference/cdialog-class.md), knihovna MFC poskytuje několik tříd odvozených z `CDialog`, které zapouzdřují běžně používaná dialogová okna, jak je znázorněno v následující tabulce. Dialogová okna zapouzdřená jsou označována jako společná dialogová okna a jsou součástí knihovny Windows Common Dialog Library (COMMDLG. DLL). Prostředky šablony dialogového okna a kód pro tyto třídy jsou k dispozici v dialogových oknech Windows Common, která jsou součástí verzí Windows 3,1 a novějších.

### <a name="common-dialog-classes"></a>Společné třídy dialogových oken

|Třída odvozeného dialogového okna|Účel|
|--------------------------|-------------|
|[CColorDialog](../mfc/reference/ccolordialog-class.md)|Umožňuje uživateli vybrat barvy.|
|[CFileDialog](../mfc/reference/cfiledialog-class.md)|Umožňuje uživateli vybrat název souboru pro otevření nebo uložení.|
|[Dialogové CFindReplaceDialog](../mfc/reference/cfindreplacedialog-class.md)|Umožňuje uživateli iniciovat operaci najít nebo nahradit v textovém souboru.|
|[CFontDialog](../mfc/reference/cfontdialog-class.md)|Umožňuje uživateli zadat písmo.|
|[CPrintDialog](../mfc/reference/cprintdialog-class.md)|Umožňuje uživateli zadat informace pro tiskovou úlohu.|
|[CPrintDialogEx](../mfc/reference/cprintdialogex-class.md)|Seznam vlastností tisku ve Windows|

Další informace o běžných třídách dialogového okna naleznete v tématu jednotlivé třídy v *Referenci knihovny MFC*. MFC také poskytuje počet standardních tříd dialogů používaných pro OLE. Informace o těchto třídách naleznete v tématu základní třída [COleDialog](../mfc/reference/coledialog-class.md)v *odkazu knihovny MFC*.

Tři ostatní třídy v knihovně MFC mají charakteristiky jako dialog. Informace o třídách [CFormView](../mfc/reference/cformview-class.md), [CRecordView](../mfc/reference/crecordview-class.md)a [CDaoRecordView](../mfc/reference/cdaorecordview-class.md)naleznete v tématu třídy v *Referenci knihovny MFC*. Informace o třídě [CDialogBar](../mfc/reference/cdialogbar-class.md)naleznete v tématu [dialogová okna](../mfc/dialog-bars.md).

## <a name="see-also"></a>Další informace najdete v tématech

[Dialogová okna](../mfc/dialog-boxes.md)<br/>
[Práce s dialogovými okny v MFC](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Dialogová okna v OLE](../mfc/dialog-boxes-in-ole.md)

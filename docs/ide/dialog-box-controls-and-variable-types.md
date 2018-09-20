---
title: Ovládací prvky dialogového okna a typy proměnných | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog box controls, member variables
- dialog box controls, variable types
- variables, dialog box control member variables
ms.assetid: f9cd9cea-45a6-4349-8358-e5efbcdcff76
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6914ab8b5838ee6bc5bb7a74004ed986efe2fcda
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373984"
---
# <a name="dialog-box-controls-and-variable-types"></a>Ovládací prvky dialogových oken a typy proměnných

Můžete použít [Průvodce přidáním členské proměnné](../ide/add-member-variable-wizard.md) přidání členské proměnné do ovládacího prvku dialogu pole vytvořené pomocí knihovny MFC. Typ ovládacího prvku, pro který přidáte členské proměnné určuje možnosti, které se zobrazí v dialogovém okně.

Následující tabulka popisuje všechny typy ovládacích prvků dialogového okna podporován v prostředí MFC a [editoru dialogového okna](../windows/dialog-editor.md)a jejich dostupné typy a hodnoty.

|Ovládací prvek|Typ ovládacího prvku|Typ řídicí proměnné|Typ hodnoty proměnné|Minimální/maximální hodnoty (pouze typ hodnoty)|
|-------------|------------------|---------------------------|-------------------------|-----------------------------------------|
|Animace ovládacího prvku|SysAnimate32|[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)|None; pouze ovládací prvek|Není k dispozici|
|Tlačítko|TLAČÍTKO|[CButton](../mfc/reference/cbutton-class.md)|None; pouze ovládací prvek|Není k dispozici|
|Zaškrtávací políčko|KONTROLA|[CButton](../mfc/reference/cbutton-class.md)|**BOOL**|Minimální hodnota/maximální hodnoty|
|Pole se seznamem|POLE SE SEZNAMEM|[CComboBox](../mfc/reference/ccombobox-class.md)|[CString –](../atl-mfc-shared/reference/cstringt-class.md)|Maximální počet znaků|
|Ovládací prvek pro výběr data|SysDateTimePick32|[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)|[CTime –](../atl-mfc-shared/reference/ctime-class.md)|Minimální hodnota/maximální hodnoty|
|Textové pole|UPRAVIT|[Cedit –](../mfc/reference/cedit-class.md)|`CString`, int, UINT, long, DWORD, float, double, BYTE, short, BOOL, `COleDateTime`, nebo **COleCurrency**|Minimální hodnota/maximální hodnoty; maximální počet znaků: některé podpory|
|Ovládacího prvku klávesová zkratka|msctls_hotkey32|[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)|None; pouze ovládací prvek|Není k dispozici|
|Pole se seznamem|LISTBOX|[Clistbox –](../mfc/reference/clistbox-class.md)|`CString`|Maximální počet znaků|
|Ovládací prvek seznamu|SysListView32|[CListCtrl](../mfc/reference/clistctrl-class.md)|None; pouze ovládací prvek|Není k dispozici|
|Ovládací prvek měsíční kalendář|SysMonthCal32|[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)|`CTime`|Minimální hodnota/maximální hodnoty|
|Ovládací prvek průběh|msctls_progress32|[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)|None; pouze ovládací prvek|Není k dispozici|
|Ovládacího prvku Rich Edit 2|RichEdit20A|[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)|`CString`|Maximální počet znaků|
|Ovládací prvek pro úpravy s formátováním|RICHEDIT|`CRichEditCtrl`|`CString`|Maximální počet znaků|
|Posuvník (svislý nebo vodorovný|POSUVNÍK|[CScrollBar](../mfc/reference/cscrollbar-class.md)|`int`|Minimální hodnota/maximální hodnoty|
|Posuvník|msctls_trackbar32|[CSliderCtrl](../mfc/reference/csliderctrl-class.md)|`int`|Minimální hodnota/maximální hodnoty|
|Ovládací prvek typu číselník|msctls_updown32|[Cspinbuttonctrl –](../mfc/reference/cspinbuttonctrl-class.md)|None; pouze ovládací prvek|Není k dispozici|
|Ovládací prvek karty|SysTabControl32|[CTabCtrl](../mfc/reference/ctabctrl-class.md)|None; pouze ovládací prvek|Není k dispozici|
|Ovládací prvek stromu|SysTreeView32|[CTreeCtrl](../mfc/reference/ctreectrl-class.md)|None; pouze ovládací prvek|Není k dispozici|

## <a name="see-also"></a>Viz také

[Přidání členské proměnné](../ide/adding-a-member-variable-visual-cpp.md)
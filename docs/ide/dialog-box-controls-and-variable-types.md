---
title: Ovládací prvky dialogové okno a typy proměnných | Microsoft Docs
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
ms.openlocfilehash: f2fbae37072f50898181334a9059a7dc9c6a83a9
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "33335062"
---
# <a name="dialog-box-controls-and-variable-types"></a>Ovládací prvky dialogových oken a typy proměnných
Můžete použít [Průvodce přidáním členské proměnné](../ide/add-member-variable-wizard.md) přidání členské proměnné na ovládací prvek dialogového okna vytvořené pomocí knihovny MFC. Typ ovládacího prvku, pro kterou přidáte členské proměnné určuje možnosti, které se zobrazují v dialogovém okně.  
  
 Následující tabulka popisuje všechny typy ovládacích prvků dialogové okno podporované v prostředí MFC a [editoru dialogového okna](../windows/dialog-editor.md)a jejich dostupné typy a hodnoty.  
  
|Ovládací prvek|– Typ ovládacího prvku|Proměnné – typ ovládacího prvku|Typ hodnoty proměnné|Minimální nebo maximální hodnoty (pouze typ hodnoty)|  
|-------------|------------------|---------------------------|-------------------------|-----------------------------------------|  
|Ovládacího prvku animace|SysAnimate32|[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)|None; pouze ovládací prvek|Není k dispozici|  
|Tlačítko|TLAČÍTKO|[CButton](../mfc/reference/cbutton-class.md)|None; pouze ovládací prvek|Není k dispozici|  
|Zaškrtávací políčko|KONTROLA|[CButton](../mfc/reference/cbutton-class.md)|**BOOL**|Minimální hodnota nebo maximální hodnota|  
|Pole se seznamem|POLE SE SEZNAMEM|[CComboBox](../mfc/reference/ccombobox-class.md)|[CString](../atl-mfc-shared/reference/cstringt-class.md)|Maximální počet znaků|  
|Čas pro výběr data|SysDateTimePick32|[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)|[CTime –](../atl-mfc-shared/reference/ctime-class.md)|Minimální hodnota nebo maximální hodnota|  
|Textové pole|UPRAVIT|[CEdit](../mfc/reference/cedit-class.md)|`CString`, int, UINT, long, DWORD, float, double, BYTE, řečeno, BOOL, `COleDateTime`, nebo **COleCurrency**|Minimální hodnota nebo maximální hodnota; Některé podporují maximální počet znaků|  
|Ovládací prvek Klávesová zkratka|msctls_hotkey32|[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)|None; pouze ovládací prvek|Není k dispozici|  
|Pole se seznamem|LISTBOX|[Clistbox –](../mfc/reference/clistbox-class.md)|`CString`|Maximální počet znaků|  
|Ovládací prvek seznamu|SysListView32|[CListCtrl](../mfc/reference/clistctrl-class.md)|None; pouze ovládací prvek|Není k dispozici|  
|Ovládací prvek měsíční kalendář|SysMonthCal32|[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)|`CTime`|Minimální hodnota nebo maximální hodnota|  
|Ovládací prvek průběh|msctls_progress32|[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)|None; pouze ovládací prvek|Není k dispozici|  
|Ovládací prvek Rich Edit 2|RichEdit20A|[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)|`CString`|Maximální počet znaků|  
|Ovládací prvek pro úpravy s formátováním|RICHEDIT|`CRichEditCtrl`|`CString`|Maximální počet znaků|  
|Posuvník (vertikální nebo horizontální|SCROLLBAR|[CScrollBar](../mfc/reference/cscrollbar-class.md)|`int`|Minimální hodnota nebo maximální hodnota|  
|Posuvník|msctls_trackbar32|[CSliderCtrl](../mfc/reference/csliderctrl-class.md)|`int`|Minimální hodnota nebo maximální hodnota|  
|Ovládací prvek typu číselník|msctls_updown32|[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)|None; pouze ovládací prvek|Není k dispozici|  
|Ovládací prvek karty|SysTabControl32|[CTabCtrl](../mfc/reference/ctabctrl-class.md)|None; pouze ovládací prvek|Není k dispozici|  
|Ovládací prvek stromu|SysTreeView32|[CTreeCtrl](../mfc/reference/ctreectrl-class.md)|None; pouze ovládací prvek|Není k dispozici|  
  
## <a name="see-also"></a>Viz také  
 [Přidání členské proměnné](../ide/adding-a-member-variable-visual-cpp.md)
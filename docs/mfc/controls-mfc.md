---
title: "Ovládací prvky (MFC) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Windows common controls [MFC]
- common controls [MFC]
- controls [MFC]
ms.assetid: b2842884-6435-4b8f-933b-21671bf8af95
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b18979ec502ea645cf8cdac39ca9ea75cb229e61
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2018
---
# <a name="controls-mfc"></a>Ovládací prvky (MFC)
Ovládací prvky jsou objekty, které mohou uživatelé komunikovat s zadejte nebo pracovat s daty. Běžně zobrazují se v dialogových oknech nebo na panely nástrojů. Toto téma rodiny obsahuje tři hlavní typy ovládacích prvků:  
  
-   Běžné ovládací prvky Windows, včetně ovládací prvky vykreslované uživatelem  
  
-   ActiveX – ovládací prvky  
  
-   Ostatní třídy ovládacích prvků zadaný pomocí Microsoft Foundation Class knihovny (MFC)  
  
## <a name="windows-common-controls"></a>Běžné ovládací prvky Windows  
 Operační systém Windows má vždy zadat počet běžné ovládací prvky Windows. Tyto objekty řízení jsou programovatelný a dialogové okno editor Visual C++ podporuje jejich přidání do dialogových oken. Microsoft Foundation Class Library (MFC) poskytuje třídy, které zapouzdření těchto ovládacích prvků, jak je znázorněno v tabulce [běžné ovládací prvky Windows a MFC – třídy](#_core_windows_common_controls_and_mfc_classes). (Některé položky v tabulce mají související témata, která je dále popisují. Ovládací prvky, které nemají témata najdete v dokumentaci pro třídy MFC.)  
  
 Třída [CWnd](../mfc/reference/cwnd-class.md) je základní třída všech tříd oken, včetně všech objektů třídy ovládacích prvků. 
  
## <a name="activex-controls"></a>ActiveX – ovládací prvky  
 Ovládací prvky ActiveX, dřív označované jako ovládací prvky OLE, lze v dialogových oknech v aplikacích pro Windows, nebo na stránkách HTML na webu. Další informace najdete v tématu [ovládací prvky MFC ActiveX](../mfc/mfc-activex-controls.md).  
  
## <a name="other-mfc-control-classes"></a>Ostatní třídy ovládacích prvků MFC  
 Kromě třídy, které zapouzdření všechny běžné ovládací prvky Windows a že podpory programování vlastních ovládacích prvků ActiveX (nebo použití ovládacích prvků ActiveX, které poskytl jiné) poskytuje MFC následující třídy ovládacích prvků své vlastní:  
  
-   [CBitmapButton](../mfc/reference/cbitmapbutton-class.md)  
  
-   [CCheckListBox](../mfc/reference/cchecklistbox-class.md)  
  
-   [CDragListBox](../mfc/reference/cdraglistbox-class.md)  
  
##  <a name="_core_finding_information_about_windows_common_controls"></a>Hledání informací o běžné ovládací prvky Windows  
 Následující tabulka stručně popisuje všechny běžné ovládací prvky Windows, včetně ovládacího prvku MFC obálkovou třídu.  
  
### <a name="_core_windows_common_controls_and_mfc_classes"></a>Běžné ovládací prvky Windows a MFC – třídy  
  
|Ovládací prvek|Třída knihovny MFC|Popis|Novinka v systému Windows 95|  
|-------------|---------------|-----------------|------------------------|  
|[animace](../mfc/using-canimatectrl.md)|[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)|Zobrazí po sobě jdoucích snímků video klip souborů AVI|Ano|  
|Tlačítko|[CButton](../mfc/reference/cbutton-class.md)|Tlačítek, které způsobí akce; použít i pro zaškrtávací políčka, přepínače a skupinové rámečky|Ne|  
|pole se seznamem|[CComboBox](../mfc/reference/ccombobox-class.md)|Kombinace textové pole a pole se seznamem|Ne|  
|[Výběr data a času.](../mfc/using-cdatetimectrl.md)|[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)|Umožňuje uživateli vybrat konkrétní datum nebo čas hodnota|Ano|  
|Textové pole|[CEdit](../mfc/reference/cedit-class.md)|Pole pro zadávání textu|Ne|  
|[Rozšířená pole se seznamem](../mfc/using-ccomboboxex.md)|[CComboBoxEx](../mfc/reference/ccomboboxex-class.md)|Ovládací prvek pole se seznamem s možností zobrazení obrázků|Ano|  
|[header](../mfc/using-cheaderctrl.md)|[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)|Tlačítko, které se zobrazí nad sloupec textu; Šířka textu zobrazí ovládací prvky|Ano|  
|[Klávesová zkratka](../mfc/using-chotkeyctrl.md)|[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)|Okno, které umožňuje uživateli vytvořit "klávesové zkratky" k provedení akce rychle|Ano|  
|[seznam obrázků](../mfc/using-cimagelist.md)|[CImageList](../mfc/reference/cimagelist-class.md)|Kolekce obrázků použitých ke správě velkého objemu ikony nebo bitmapy (seznamu obrázků není skutečně ovládacího prvku; podporuje seznamy používají ovládací prvky)|Ano|  
|[list](../mfc/using-clistctrl.md)|[CListCtrl](../mfc/reference/clistctrl-class.md)|Okno, které se zobrazí seznam textu pomocí ikony|Ano|  
|Pole se seznamem|[CListBox](../mfc/reference/clistbox-class.md)|Pole, která obsahuje seznam řetězců|Ne|  
|[měsíční kalendář](../mfc/using-cmonthcalctrl.md)|[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)|Ovládací prvek, který zobrazí informace o datu|Ano|  
|[průběh](../mfc/using-cprogressctrl.md)|[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)|Okno, které označuje průběh dlouhé operace|Ano|  
|[rebar](../mfc/using-crebarctrl.md)|[CRebarCtrl](../mfc/reference/crebarctrl-class.md)|Panel nástrojů, která může obsahovat další podřízené windows ve formuláři ovládací prvky|Ano|  
|[pro úpravy s formátováním](../mfc/using-cricheditctrl.md)|[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)|Okno, ve které uživatele můžete upravit pomocí znaku a formátování odstavce (viz [třídy související s ovládacími prvky upravit bohaté](../mfc/classes-related-to-rich-edit-controls.md))|Ano|  
|posuvník|[CScrollBar](../mfc/reference/cscrollbar-class.md)|Posuvník použít jako ovládací prvek v dialogovém okně (nikoli na okno)|Ne|  
|[slider](../mfc/using-csliderctrl.md)|[CSliderCtrl](../mfc/reference/csliderctrl-class.md)|Okno obsahující ovládací prvek typu jezdec s volitelnými osové značky|Ano|  
|[číselníku](../mfc/using-cspinbuttonctrl.md)|[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)|Pár šipku tlačítka uživatele můžete kliknutím přírůstek nebo snížení hodnotu|Ano|  
|static-text|[CStatic](../mfc/reference/cstatic-class.md)|Text pro označování další ovládací prvky|Ne|  
|[Stavový řádek](../mfc/using-cstatusbarctrl.md)|[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)|Okno pro zobrazení informace o stavu, podobně jako třída knihovny MFC`CStatusBar`|Ano|  
|[Karta](../mfc/using-ctabctrl.md)|[CTabCtrl](../mfc/reference/ctabctrl-class.md)|Podobá se oddělovačů v poznámkovém bloku; použít "dialogová okna karet", nebo seznam vlastností|Ano|  
|[toolbar](../mfc/using-ctoolbarctrl.md)|[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)|Okno s generování příkazového tlačítka, podobně jako třída knihovny MFC`CToolBar`|Ano|  
|[Popis tlačítka](../mfc/using-ctooltipctrl.md)|[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)|Malé místní okno, který popisuje účel tlačítka panelu nástrojů nebo jiný nástroj|Ano|  
|[strom](../mfc/using-ctreectrl.md)|[CTreeCtrl](../mfc/reference/ctreectrl-class.md)|Okno, které zobrazí hierarchické seznam položek|Ano|  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   Ovládací prvek jednotlivých: Podívejte se na tabulku [běžné ovládací prvky Windows a MFC – třídy](#_core_windows_common_controls_and_mfc_classes) v tomto tématu pro odkazy na všechny ovládací prvky  
  
-   [Příprava a použití ovládacích prvků](../mfc/making-and-using-controls.md)  
  
-   [Použití editoru dialogových oken k přidávání ovládacích prvků](../mfc/using-the-dialog-editor-to-add-controls.md)  
  
-   [Ruční přidání ovládacích prvků do dialogového okna](../mfc/adding-controls-by-hand.md)  
  
-   [Odvozování z třídy ovládacích prvků MFC – třídy ovládacích prvků](../mfc/deriving-controls-from-a-standard-control.md)  
  
-   [Použití běžných ovládacích prvků jako podřízená okna](../mfc/using-a-common-control-as-a-child-window.md)  
  
-   [Oznámení z běžných ovládacích prvků](../mfc/receiving-notification-from-common-controls.md)  
  
-   [Přidání běžných ovládacích prvků do dialogového okna](../mfc/using-common-controls-in-a-dialog-box.md).  
  
-   [Odvození ovládacího prvku ze standardního ovládacího prvku systému Windows](../mfc/deriving-controls-from-a-standard-control.md)  
  
-   [Řízení přístupu – dialogové okno s zabezpečení typů](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)  
  
-   [Příjem oznámení z běžných ovládacích prvků](../mfc/receiving-notification-from-common-controls.md)  
  
-   [Ukázky](../mfc/common-control-sample-list.md)  
  
 Informace o běžných ovládacích prvcích Windows ve Windows SDK najdete v tématu [běžné ovládací prvky](http://msdn.microsoft.com/library/windows/desktop/bb775493).  
  
## <a name="see-also"></a>Viz také  
 [Prvky uživatelského rozhraní](../mfc/user-interface-elements-mfc.md)   
 [Editor dialogových oken](../windows/dialog-editor.md)


---
title: Ovládací prvky (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- Windows common controls [MFC]
- common controls [MFC]
- controls [MFC]
ms.assetid: b2842884-6435-4b8f-933b-21671bf8af95
ms.openlocfilehash: 3155889f2fd4002286340ccec7f4a35d1a6a9c20
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508793"
---
# <a name="controls-mfc"></a>Ovládací prvky (MFC)

Ovládací prvky jsou objekty, se kterými můžou uživatelé interaktivně zadávat data a manipulovat s nimi. Obvykle se zobrazují v dialogových oknech nebo na panelech nástrojů. Tato rodina obsahuje tři hlavní druhy ovládacích prvků:

- Běžné ovládací prvky pro Windows, včetně ovládacích prvků vykreslených vlastníkem

- ActiveX – ovládací prvky

- Další třídy ovládacích prvků poskytované knihovna Microsoft Foundation Class (MFC)

## <a name="windows-common-controls"></a>Běžné ovládací prvky Windows

Operační systém Windows má vždycky k dispozici několik běžných ovládacích prvků pro Windows. Tyto řídicí objekty jsou programovatelné a editor C++ dialogových oken podporuje jejich přidání do dialogových oken. Knihovna Microsoft Foundation Class (MFC) poskytuje třídy, které zapouzdřují každý z těchto ovládacích prvků, jak je znázorněno v tabulce [běžné ovládací prvky Windows a MFC třídy](#_core_windows_common_controls_and_mfc_classes). (Některé položky v tabulce mají Příbuzná témata, která je popisují. Ovládací prvky, které nemají témata, naleznete v dokumentaci ke třídě MFC.)

Třída [CWnd](../mfc/reference/cwnd-class.md) je základní třídou všech tříd okna, včetně všech tříd ovládacích prvků.

## <a name="activex-controls"></a>ActiveX – ovládací prvky

Ovládací prvky ActiveX, dříve označované jako ovládací prvky OLE, lze použít v dialogových oknech aplikací pro systém Windows nebo na stránkách HTML na webu. Další informace naleznete v tématu [ovládací prvky MFC ActiveX](../mfc/mfc-activex-controls.md).

## <a name="other-mfc-control-classes"></a>Jiné třídy ovládacích prvků MFC

Kromě tříd, které zapouzdřují všechny běžné ovládací prvky systému Windows a podporují programování pro vlastní ovládací prvky ActiveX (nebo použití ovládacích prvků ActiveX dodaných ostatními), knihovna MFC poskytuje následující třídy ovládacích prvků:

- [CBitmapButton](../mfc/reference/cbitmapbutton-class.md)

- [CCheckListBox](../mfc/reference/cchecklistbox-class.md)

- [CDragListBox](../mfc/reference/cdraglistbox-class.md)

##  <a name="_core_finding_information_about_windows_common_controls"></a>Hledání informací o běžných ovládacích prvcích Windows

Následující tabulka stručně popisuje všechny běžné ovládací prvky systému Windows, včetně obálkové třídy MFC ovládacího prvku.

### <a name="_core_windows_common_controls_and_mfc_classes"></a>Běžné ovládací prvky Windows a třídy MFC

|Control|MFC – třída|Popis|Novinka ve Windows 95|
|-------------|---------------|-----------------|------------------------|
|[animaci](../mfc/using-canimatectrl.md)|[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)|Zobrazí po sobě jdoucí snímky videoklipu AVI.|Ano|
|tlačítko|[CButton](../mfc/reference/cbutton-class.md)|Pushbuttons, které způsobují akci. používá se také pro zaškrtávací políčka, přepínače a skupinová pole.|Ne|
|pole se seznamem|[CComboBox](../mfc/reference/ccombobox-class.md)|Kombinace pole pro úpravy a pole se seznamem|Ne|
|[Výběr data a času](../mfc/using-cdatetimectrl.md)|[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)|Umožňuje uživateli zvolit určitou hodnotu data a času.|Ano|
|textové pole|[CEdit](../mfc/reference/cedit-class.md)|Pole pro zadání textu|Ne|
|[Rozšířené pole se seznamem](../mfc/using-ccomboboxex.md)|[CComboBoxEx](../mfc/reference/ccomboboxex-class.md)|Ovládací prvek pole se seznamem s možností zobrazení obrázků|Ano|
|[header](../mfc/using-cheaderctrl.md)|[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)|Tlačítko, které se zobrazí nad sloupcem textu; Určuje šířku zobrazeného textu.|Ano|
|[hotkey](../mfc/using-chotkeyctrl.md)|[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)|Okno, které umožňuje uživateli vytvořit rychlý klíč k provedení akce|Ano|
|[seznam obrázků](../mfc/using-cimagelist.md)|[Atributu CImageList](../mfc/reference/cimagelist-class.md)|Kolekce imagí sloužících ke správě rozsáhlých sad ikon nebo rastrových obrázků (seznam obrázků není ve skutečnosti ovládací prvek, který podporuje seznamy používané jinými ovládacími prvky)|Ano|
|[list](../mfc/using-clistctrl.md)|[CListCtrl](../mfc/reference/clistctrl-class.md)|Okno, které zobrazuje seznam textu s ikonami|Ano|
|seznam|[CListBox –](../mfc/reference/clistbox-class.md)|Box, který obsahuje seznam řetězců|Ne|
|[měsíční kalendář](../mfc/using-cmonthcalctrl.md)|[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)|Ovládací prvek, který zobrazuje informace o datu|Ano|
|[přejde](../mfc/using-cprogressctrl.md)|[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)|Okno, které indikuje průběh dlouhé operace|Ano|
|[matrice](../mfc/using-crebarctrl.md)|[CRebarCtrl](../mfc/reference/crebarctrl-class.md)|Panel nástrojů, který může obsahovat další podřízená okna ve formě ovládacích prvků|Ano|
|[úpravy s bohatým obsahem](../mfc/using-cricheditctrl.md)|[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)|Okno, ve kterém může uživatel upravit pomocí formátování znaků a odstavců (viz [třídy související s ovládacími prvky pro úpravy](../mfc/classes-related-to-rich-edit-controls.md)s formátováním)|Ano|
|posuvník|[CScrollBar](../mfc/reference/cscrollbar-class.md)|Posuvník použitý jako ovládací prvek v dialogovém okně (ne v okně)|Ne|
|[slider](../mfc/using-csliderctrl.md)|[CSliderCtrl](../mfc/reference/csliderctrl-class.md)|Okno obsahující ovládací prvek posuvník s volitelnými značkami|Ano|
|[tlačítko číselníku](../mfc/using-cspinbuttonctrl.md)|[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)|Dvojice tlačítek s šipkou může uživatel kliknout na zvýšení nebo snížení hodnoty.|Ano|
|statický text|[CStatic](../mfc/reference/cstatic-class.md)|Text pro označování jiných ovládacích prvků|Ne|
|[stavový řádek](../mfc/using-cstatusbarctrl.md)|[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)|Okno pro zobrazení informací o stavu, podobně jako třída MFC`CStatusBar`|Ano|
|[tab](../mfc/using-ctabctrl.md)|[CTabCtrl](../mfc/reference/ctabctrl-class.md)|Podobá se oddělovači v poznámkovém bloku; používá se v dialogovém okně s kartami nebo na seznam vlastností.|Ano|
|[toolbar](../mfc/using-ctoolbarctrl.md)|[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)|Okno s tlačítky pro generování příkazů, podobně jako třída MFC`CToolBar`|Ano|
|[Popis nástroje](../mfc/using-ctooltipctrl.md)|[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)|Malé automaticky otevírané okno, které popisuje účel tlačítka panelu nástrojů nebo jiného nástroje.|Ano|
|[strukturu](../mfc/using-ctreectrl.md)|[CTreeCtrl](../mfc/reference/ctreectrl-class.md)|Okno, které zobrazuje hierarchický seznam položek|Ano|

### <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace

- Individuální ovládací prvek: viz tabulka [běžné ovládací prvky Windows a MFC třídy](#_core_windows_common_controls_and_mfc_classes) v tomto tématu pro odkazy na všechny ovládací prvky

- [Vytváření a používání ovládacích prvků](../mfc/making-and-using-controls.md)

- [Použití editoru dialogových oken k přidávání ovládacích prvků](../mfc/using-the-dialog-editor-to-add-controls.md)

- [Ruční přidání ovládacích prvků do dialogového okna](../mfc/adding-controls-by-hand.md)

- [Odvození řídicích tříd z tříd ovládacích prvků MFC](../mfc/deriving-controls-from-a-standard-control.md)

- [Použití běžných ovládacích prvků jako podřízených oken](../mfc/using-a-common-control-as-a-child-window.md)

- [Oznámení z běžných ovládacích prvků](../mfc/receiving-notification-from-common-controls.md)

- [Přidejte do dialogového okna běžné ovládací prvky](../mfc/using-common-controls-in-a-dialog-box.md).

- [Odvodit ovládací prvek ze standardního ovládacího prvku Windows](../mfc/deriving-controls-from-a-standard-control.md)

- [Přístup k ovládacím prvkům dialogových oken pomocí typu zabezpečení](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)

- [Příjem zpráv s oznámením z běžných ovládacích prvků](../mfc/receiving-notification-from-common-controls.md)

- [Ukázky](../mfc/common-control-sample-list.md)

Informace o běžných ovládacích prvcích Windows v Windows SDK najdete v tématu [běžné ovládací prvky](/windows/win32/Controls/common-controls-intro).

## <a name="see-also"></a>Viz také:

[Prvky uživatelského rozhraní](../mfc/user-interface-elements-mfc.md)<br/>
[Editor dialogových oken](../windows/dialog-editor.md)

---
title: Ovládací prvky (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- Windows common controls [MFC]
- common controls [MFC]
- controls [MFC]
ms.assetid: b2842884-6435-4b8f-933b-21671bf8af95
ms.openlocfilehash: c0738128d20839046e0885e7489b494d84349e4d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304532"
---
# <a name="controls-mfc"></a>Ovládací prvky (MFC)

Ovládací prvky jsou objekty, které mohou uživatelé komunikovat s a zadejte skript nebo manipulaci s daty. Běžně zobrazují v dialogových oknech nebo na panely nástrojů. Toto téma řady zahrnuje tři hlavní typy ovládacích prvků:

- Windows běžných ovládacích prvků, včetně ovládací prvky vykreslované uživatelem

- ActiveX – ovládací prvky

- Další ovládací prvek třídy zadané ve třídy knihovny MFC (Microsoft Foundation)

## <a name="windows-common-controls"></a>Běžné ovládací prvky Windows

Operační systém Windows má vždy k dispozici řadu běžných ovládacích prvků Windows. Tyto objekty ovládacího prvku jsou programovatelné a dialogové okno editor jazyka Visual C++ podporuje přidání do dialogových oknech. Třídy knihovny MFC (Microsoft Foundation) poskytuje třídy, které zapouzdřit každý z těchto ovládacích prvků, jak je znázorněno v tabulce [třídy knihovny MFC a běžných ovládacích prvků Windows](#_core_windows_common_controls_and_mfc_classes). (Některé položky v tabulce mají související témata, která je dále popisují. Pro ovládací prvky, které nemají témata najdete v dokumentaci pro třídy knihovny MFC.)

Třída [CWnd](../mfc/reference/cwnd-class.md) je základní třída všech tříd oken, včetně všech objektů třídy ovládacích prvků.

## <a name="activex-controls"></a>ActiveX – ovládací prvky

Ovládací prvky ActiveX, dřív označované jako ovládací prvky OLE, je možné v dialogových oknech v aplikacích pro Windows nebo na stránkách HTML na webu. Další informace najdete v tématu [ovládací prvky MFC ActiveX](../mfc/mfc-activex-controls.md).

## <a name="other-mfc-control-classes"></a>Jiné třídy ovládacích prvků MFC

Kromě tříd, které provádí zapouzdření všechny běžné ovládací prvky Windows a tuto podporu programování vlastních ovládacích prvků ActiveX (nebo pomocí poskytnutých ostatní ovládací prvky ActiveX) MFC poskytuje následující třídy ovládacího prvku vlastní:

- [CBitmapButton](../mfc/reference/cbitmapbutton-class.md)

- [CCheckListBox](../mfc/reference/cchecklistbox-class.md)

- [CDragListBox](../mfc/reference/cdraglistbox-class.md)

##  <a name="_core_finding_information_about_windows_common_controls"></a> Hledání informací o běžných ovládacích prvků Windows

Následující tabulka stručně popisuje každý Windows běžných ovládacích prvků, včetně ovládacích prvků MFC obálkovou třídu.

### <a name="_core_windows_common_controls_and_mfc_classes"></a>  Třídy knihovny MFC a běžné ovládací prvky Windows

|Control|MFC class|Popis|Nové ve Windows 95|
|-------------|---------------|-----------------|------------------------|
|[Animace](../mfc/using-canimatectrl.md)|[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)|Zobrazí po sobě jdoucích snímků AVI videoklipu|Ano|
|Tlačítko|[CButton](../mfc/reference/cbutton-class.md)|Tlačítek, které způsobují akci; také používá pro zaškrtávací políčka, přepínače a skupinové rámečky|Ne|
|pole se seznamem|[CComboBox](../mfc/reference/ccombobox-class.md)|Do textového pole a pole se seznamem|Ne|
|[Výběr data a času](../mfc/using-cdatetimectrl.md)|[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)|Umožňuje uživateli zvolit konkrétní datum nebo čas|Ano|
|Textové pole|[CEdit](../mfc/reference/cedit-class.md)|Pole pro zadávání textu|Ne|
|[Rozšířené pole se seznamem](../mfc/using-ccomboboxex.md)|[CComboBoxEx](../mfc/reference/ccomboboxex-class.md)|Ovládací prvek pole se seznamem se schopnost zobrazit obrázky|Ano|
|[header](../mfc/using-cheaderctrl.md)|[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)|Tlačítko, které se zobrazí nad sloupcem textu. Šířka ovládacích prvků textu zobrazeného|Ano|
|[hotkey](../mfc/using-chotkeyctrl.md)|[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)|Okno, které umožňuje uživateli vytvořit "klávesové zkratky" k rychlému provádění akce|Ano|
|[seznam obrázků](../mfc/using-cimagelist.md)|[CImageList](../mfc/reference/cimagelist-class.md)|Kolekce obrazů používá ke správě velkých sad ikony nebo rastrové obrázky (seznam obrázků není ve skutečnosti ovládací prvek; podporuje seznamy, které používají ovládací prvky)|Ano|
|[list](../mfc/using-clistctrl.md)|[CListCtrl](../mfc/reference/clistctrl-class.md)|Okno, které se zobrazí seznam text s ikonami|Ano|
|Pole se seznamem|[CListBox](../mfc/reference/clistbox-class.md)|Pole, které obsahuje seznam řetězců|Ne|
|[Měsíční kalendář](../mfc/using-cmonthcalctrl.md)|[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)|Ovládací prvek, který se zobrazí informace o datu|Ano|
|[progress](../mfc/using-cprogressctrl.md)|[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)|Okno, které označuje průběh dlouhá operace|Ano|
|[rebar](../mfc/using-crebarctrl.md)|[CRebarCtrl](../mfc/reference/crebarctrl-class.md)|Panel nástrojů, který může obsahovat další podřízená okna do formuláře ovládací prvky|Ano|
|[Pro úpravy s formátováním](../mfc/using-cricheditctrl.md)|[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)|Okno, v které uživatel může upravovat pomocí formátování znaků a odstavců (viz [třídy související s formátováním upravit ovládací prvky](../mfc/classes-related-to-rich-edit-controls.md))|Ano|
|posuvník|[CScrollBar](../mfc/reference/cscrollbar-class.md)|Posuvník použít jako ovládací prvek uvnitř dialogové okno (nikoli na okno)|Ne|
|[slider](../mfc/using-csliderctrl.md)|[CSliderCtrl](../mfc/reference/csliderctrl-class.md)|Okno obsahující ovládací prvek posuvník s volitelným osové značky|Ano|
|[číselníku](../mfc/using-cspinbuttonctrl.md)|[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)|Pár uživatel tlačítek šipku můžete kliknutím přírůstek nebo snížení hodnoty|Ano|
|static-text|[Cstatic –](../mfc/reference/cstatic-class.md)|Text pro označování popisky další ovládací prvky|Ne|
|[status bar](../mfc/using-cstatusbarctrl.md)|[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)|Okno pro zobrazení informací o stavu, podobně jako třída knihovny MFC `CStatusBar`|Ano|
|[tab](../mfc/using-ctabctrl.md)|[CTabCtrl](../mfc/reference/ctabctrl-class.md)|Obdobná oddělovačů v poznámkovém bloku; použít "dialogová okna Karta", nebo seznam vlastností|Ano|
|[toolbar](../mfc/using-ctoolbarctrl.md)|[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)|Okno s generováním příkazového tlačítka, podobně jako třída knihovny MFC `CToolBar`|Ano|
|[Popis tlačítka](../mfc/using-ctooltipctrl.md)|[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)|Malého vyskakovacího okna, který popisuje účel tlačítka panelu nástrojů nebo jiný nástroj|Ano|
|[strom](../mfc/using-ctreectrl.md)|[CTreeCtrl](../mfc/reference/ctreectrl-class.md)|Okno, které zobrazí hierarchické seznam položek|Ano|

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- Jednotlivé ovládací prvky: viz tabulka [třídy knihovny MFC a běžných ovládacích prvků Windows](#_core_windows_common_controls_and_mfc_classes) v tomto tématu pro odkazy na všechny ovládací prvky

- [Příprava a použití ovládacích prvků](../mfc/making-and-using-controls.md)

- [Použití editoru dialogových oken k přidávání ovládacích prvků](../mfc/using-the-dialog-editor-to-add-controls.md)

- [Ruční přidání ovládacích prvků do dialogového okna](../mfc/adding-controls-by-hand.md)

- [Odvození třídy ovládacích prvků z třídy ovládacích prvků MFC](../mfc/deriving-controls-from-a-standard-control.md)

- [Použití běžných ovládacích prvků jako podřízených oken](../mfc/using-a-common-control-as-a-child-window.md)

- [Oznámení z běžných ovládacích prvků](../mfc/receiving-notification-from-common-controls.md)

- [Do dialogového okna Přidat běžné ovládací prvky](../mfc/using-common-controls-in-a-dialog-box.md).

- [Ovládací prvek odvozen ze standardního ovládacího prvku Windows](../mfc/deriving-controls-from-a-standard-control.md)

- [Ovládací prvky dialogového okna přístup s bezpečností typů](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)

- [Příjem oznámení z běžných ovládacích prvků](../mfc/receiving-notification-from-common-controls.md)

- [Ukázky](../mfc/common-control-sample-list.md)

Informace o běžných ovládacích prvků Windows v sadě Windows SDK najdete v tématu [běžné ovládací prvky](/windows/desktop/Controls/common-controls-intro).

## <a name="see-also"></a>Viz také:

[Prvky uživatelského rozhraní](../mfc/user-interface-elements-mfc.md)<br/>
[Editor dialogových oken](../windows/dialog-editor.md)

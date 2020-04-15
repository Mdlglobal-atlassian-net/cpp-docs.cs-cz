---
title: Ovládací prvky (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- Windows common controls [MFC]
- common controls [MFC]
- controls [MFC]
ms.assetid: b2842884-6435-4b8f-933b-21671bf8af95
ms.openlocfilehash: 454a76e8fdf55f43d75abb63d7d98a9fe4926127
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365328"
---
# <a name="controls-mfc"></a>Ovládací prvky (MFC)

Ovládací prvky jsou objekty, se kterými mohou uživatelé pracovat za účelem zadávání dat nebo manipulace s nimi. Obvykle se objevují v dialogových oknech nebo na panelech nástrojů. Toto téma rodina zahrnuje tři hlavní druhy ovládacích prvků:

- Běžné ovládací prvky systému Windows, včetně ovládacích prvků tažených vlastníkem

- ActiveX – ovládací prvky

- Další třídy řízení poskytované knihovnou tříd Microsoft Foundation (MFC)

## <a name="windows-common-controls"></a>Běžné ovládací prvky systému Windows

Operační systém Windows vždy poskytoval řadu běžných ovládacích prvků systému Windows. Tyto řídicí objekty jsou programovatelné a dialogový editor Visual C++ podporuje jejich přidávání do dialogových oken. Knihovna mfc (Microsoft Foundation Class Library) poskytuje třídy, které zapouzdřují každý z těchto ovládacích prvků, jak je znázorněno v tabulce [Windows Common Controls a MFC třídy](#_core_windows_common_controls_and_mfc_classes). (Některé položky v tabulce mají související témata, která je dále popisují. Ovládací prvky, které postrádají témata, naleznete v dokumentaci pro třídu knihovny MFC.)

Třída [CWnd](../mfc/reference/cwnd-class.md) je základní třída všech tříd oken, včetně všech tříd ovládacího prvku.

## <a name="activex-controls"></a>ActiveX – ovládací prvky

Ovládací prvky ActiveX, dříve označované jako ovládací prvky OLE, lze použít v dialogových oknech v aplikacích pro systém Windows nebo na stránkách HTML na webu. Další informace naleznete v tématu [MFC ActiveX Controls](../mfc/mfc-activex-controls.md).

## <a name="other-mfc-control-classes"></a>Jiné třídy řízení knihovny MFC

Kromě tříd, které zapouzdřují všechny běžné ovládací prvky systému Windows a které podporují programování vlastních ovládacích prvků ActiveX (nebo použití ovládacích prvků ActiveX dodávaných jinými uživateli), poskytuje knihovna MFC vlastní následující třídy ovládacích prvků:

- [CBitmapButton](../mfc/reference/cbitmapbutton-class.md)

- [CCheckListBox](../mfc/reference/cchecklistbox-class.md)

- [CDragListBox](../mfc/reference/cdraglistbox-class.md)

## <a name="finding-information-about-windows-common-controls"></a><a name="_core_finding_information_about_windows_common_controls"></a>Hledání informací o běžných ovládacích prvcích systému Windows

Níže uvedená tabulka stručně popisuje každý z běžných ovládacích prvků systému Windows, včetně obálky knihovny MFC třídy ovládacího prvku.

### <a name="windows-common-controls-and-mfc-classes"></a><a name="_core_windows_common_controls_and_mfc_classes"></a>Běžné ovládací prvky systému Windows a třídy knihovny MFC

|Řízení|Třída Knihovny MFC|Popis|Novinka v systému Windows 95|
|-------------|---------------|-----------------|------------------------|
|[Animace](../mfc/using-canimatectrl.md)|[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)|Zobrazí po sobě jdoucí snímky videoklipu AVI.|Ano|
|.|[CButton](../mfc/reference/cbutton-class.md)|Tlačítka, která způsobují akci; Používá se také pro zaškrtávací políčka, přepínací tlačítka a skupinová pole|Ne|
|pole se seznamem|[CComboBox](../mfc/reference/ccombobox-class.md)|Kombinace textového pole a seznamu|Ne|
|[výběr data a času](../mfc/using-cdatetimectrl.md)|[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)|Umožňuje uživateli zvolit konkrétní hodnotu data nebo času.|Ano|
|pole pro úpravy|[CEditovat](../mfc/reference/cedit-class.md)|Pole pro zadávání textu|Ne|
|[rozšířené pole se seznamem](../mfc/using-ccomboboxex.md)|[CComboBoxEx](../mfc/reference/ccomboboxex-class.md)|Ovládací prvek se seznamem se schopností zobrazovat obrázky|Ano|
|[Záhlaví](../mfc/using-cheaderctrl.md)|[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)|Tlačítko, které se zobrazí nad sloupcem textu; řídí šířku zobrazeného textu|Ano|
|[Hotkey](../mfc/using-chotkeyctrl.md)|[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)|Okno, které umožňuje uživateli vytvořit "klávesovou zkratku" pro rychlé provedení akce|Ano|
|[seznam obrázků](../mfc/using-cimagelist.md)|[Seznam CImageList](../mfc/reference/cimagelist-class.md)|Kolekce obrázků používaných ke správě velkých sad ikon nebo bitmap (seznam obrázků není ve skutečnosti ovládací prvek; podporuje seznamy používané jinými ovládacími prvky)|Ano|
|[list](../mfc/using-clistctrl.md)|[CListCtrl](../mfc/reference/clistctrl-class.md)|Okno, ve které se zobrazuje seznam textu s ikonami|Ano|
|seznam|[CListBox](../mfc/reference/clistbox-class.md)|Pole obsahující seznam řetězců|Ne|
|[měsíční kalendář](../mfc/using-cmonthcalctrl.md)|[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)|Ovládací prvek, který zobrazuje informace o datu|Ano|
|[Pokroku](../mfc/using-cprogressctrl.md)|[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)|Okno, které označuje průběh dlouhé operace|Ano|
|[Prutu](../mfc/using-crebarctrl.md)|[CRebarCtrl](../mfc/reference/crebarctrl-class.md)|Panel nástrojů, který může obsahovat další podřízená okna ve formě ovládacích prvků|Ano|
|[bohaté úpravy](../mfc/using-cricheditctrl.md)|[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)|Okno, ve kterém může uživatel upravovat pomocí formátování znaků a odstavců (viz [Třídy související s ovládacími prvky pro úpravy rich](../mfc/classes-related-to-rich-edit-controls.md))|Ano|
|posuvník|[CScrollBar](../mfc/reference/cscrollbar-class.md)|Posuvník používaný jako ovládací prvek uvnitř dialogového okna (ne v okně)|Ne|
|[Jezdec](../mfc/using-csliderctrl.md)|[CSliderCtrl](../mfc/reference/csliderctrl-class.md)|Okno obsahující posuvník s volitelnými značkami|Ano|
|[tlačítko pro odstřeďování](../mfc/using-cspinbuttonctrl.md)|[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)|Dvojice tlačítek se šipkami, na které může uživatel kliknout, aby zineklinebo zmenšoval hodnotu|Ano|
|statický text|[CStatic](../mfc/reference/cstatic-class.md)|Text pro označení jiných ovládacích prvků|Ne|
|[Stavovém](../mfc/using-cstatusbarctrl.md)|[CStavový panel](../mfc/reference/cstatusbarctrl-class.md)|Okno pro zobrazení informací o stavu, podobně jako třída Knihovny MFC`CStatusBar`|Ano|
|[Kartě](../mfc/using-ctabctrl.md)|[CTabCtrl](../mfc/reference/ctabctrl-class.md)|Analogické s děliči v notebooku; používá se v dialogových oknech "tabulátory" nebo v seznamech vlastností|Ano|
|[Panelu nástrojů](../mfc/using-ctoolbarctrl.md)|[CtoolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)|Okno s tlačítky generujícími příkazy, podobné třídě Knihovny MFC`CToolBar`|Ano|
|[tip nástroje](../mfc/using-ctooltipctrl.md)|[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)|Malé vyskakovací okno, které popisuje účel tlačítka panelu nástrojů nebo jiného nástroje|Ano|
|[strom](../mfc/using-ctreectrl.md)|[CTreeCtrl](../mfc/reference/ctreectrl-class.md)|Okno, které zobrazuje hierarchický seznam položek|Ano|

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o

- Individuální ovládací prvek: v tabulce [Windows Common Controls a MFC Classes](#_core_windows_common_controls_and_mfc_classes) v tomto tématu naleznete odkazy na všechny ovládací prvky.

- [Vytváření a používání ovládacích prvků](../mfc/making-and-using-controls.md)

- [Přidání ovládacích prvků pomocí editoru dialogů](../mfc/using-the-dialog-editor-to-add-controls.md)

- [Ruční přidávání ovládacích prvků do dialogového okna](../mfc/adding-controls-by-hand.md)

- [Odvození kontrolních tříd z řídicích tříd knihovny MFC](../mfc/deriving-controls-from-a-standard-control.md)

- [Použití běžných ovládacích prvků jako podřízených oken](../mfc/using-a-common-control-as-a-child-window.md)

- [Oznámení z běžných ovládacích prvků](../mfc/receiving-notification-from-common-controls.md)

- [Přidání běžných ovládacích prvků do dialogového okna](../mfc/using-common-controls-in-a-dialog-box.md).

- [Odvození ovládacího prvku ze standardního ovládacího prvku systému Windows](../mfc/deriving-controls-from-a-standard-control.md)

- [Přístup k ovládacím prvkům dialogového okna s bezpečností typů](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)

- [Příjem oznámení z běžných ovládacích prvků](../mfc/receiving-notification-from-common-controls.md)

- [ukázky](../mfc/common-control-sample-list.md)

Informace o běžných ovládacích prvcích systému Windows v sadě Windows SDK naleznete v [tématu Common Controls](/windows/win32/Controls/common-controls-intro).

## <a name="see-also"></a>Viz také

[Prvky uživatelského rozhraní](../mfc/user-interface-elements-mfc.md)<br/>
[Editor dialogových oken](../windows/dialog-editor.md)

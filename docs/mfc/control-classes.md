---
title: Ovládací prvek třídy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.control
dev_langs:
- C++
helpviewer_keywords:
- static display controls [MFC]
- control classes [MFC]
- buttons, MFC control classes
- controls [MFC], MFC control classes
- controls [MFC]
- list boxes [MFC], MFC control classes
- control classes [MFC], MFC
- text, controls for input [MFC]
- user input [MFC], MFC control classes
ms.assetid: f9876606-9f5b-44cb-9135-213298d1df8f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a159677ffa12961e7f065b2cba2b1287c8ef7a58
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432455"
---
# <a name="control-classes"></a>Třídy ovládacích prvků

Třídy ovládacích prvků zapouzdřit širokou škálu standardní ovládací prvky Windows od ovládacích prvků statického textu do ovládacích prvků strom. Kromě toho knihovna MFC poskytuje některé nové ovládací prvky, včetně tlačítka s pruhy rastrové obrázky a ovládací prvek.

Ovládací prvky, jejichž názvy tříd končí "**Ctrl**" byly Novinky ve Windows 95 a Windows NT verze 3.51, aktualizace.

## <a name="static-display-controls"></a>Statické ovládací prvky zobrazení

[Cstatic –](../mfc/reference/cstatic-class.md)<br/>
Statické zobrazení okna. Statické ovládací prvky se používají k popisku, pole nebo oddělení další ovládací prvky v dialogovém okně. Může také zobrazit grafické obrázky místo textu nebo pole.

## <a name="text-controls"></a>Textových ovládacích prvků

[Cedit –](../mfc/reference/cedit-class.md)<br/>
Okno aplikace upravitelný text ovládacího prvku. Upravit ovládací prvky se používají tak, aby přijímal textový vstup od uživatele.

[Cipaddressctrl –](../mfc/reference/cipaddressctrl-class.md)<br/>
Do textového pole podporuje pro manipulaci s adresy Internet Protocol (IP).

[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)<br/>
Ovládací prvek, ve kterém můžete uživatele zadat a upravit text. Na rozdíl od ovládacího prvku zapouzdřena v `CEdit`, ovládací prvek RTF podporuje znak a formátování odstavce a objekty OLE.

## <a name="controls-that-represent-numbers"></a>Ovládací prvky, které představují číslice

[CSliderCtrl](../mfc/reference/csliderctrl-class.md)<br/>
Ovládací prvek obsahující ovládací prvek posuvník, který uživatel přesune výběr hodnotu nebo sadu hodnot.

[Cspinbuttonctrl –](../mfc/reference/cspinbuttonctrl-class.md)<br/>
Zvýší nebo sníží hodnotu může uživatel kliknout pár tlačítek.

[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)<br/>
Zobrazí obdélníku, který je vyplněný postupně zleva doprava a informace o průběhu operace.

[CScrollBar](../mfc/reference/cscrollbar-class.md)<br/>
Okno ovládacího prvku posuvníku. Třída poskytuje funkce pro posuvník pro použití jako ovládací prvek v okně, pomocí kterého může uživatel zadat pozici v rámci rozsahu nebo dialogové okno.

## <a name="buttons"></a>Tlačítka

[CButton](../mfc/reference/cbutton-class.md)<br/>
Okno Ovládací prvek tlačítko. Třída poskytuje programové rozhraní pro tlačítko, zaškrtávací políčko nebo přepínací tlačítka v okně nebo dialogové okno.

[CBitmapButton](../mfc/reference/cbitmapbutton-class.md)<br/>
Tlačítko s rastrový obrázek, ne textový popisek.

## <a name="lists"></a>Seznamy

[Clistbox –](../mfc/reference/clistbox-class.md)<br/>
Okno ovládacího prvku pole se seznamem. Seznamu se zobrazí seznam položek, které uživatel může zobrazit a vybrat.

[Cdraglistbox –](../mfc/reference/cdraglistbox-class.md)<br/>
Poskytuje funkce pro pole se seznamem Windows; Umožňuje uživateli seznam položek pole, jako jsou názvy souborů a řetězcové literály, přesouvat v rámci pole se seznamem. Pole se seznamem díky tomu jsou užitečné pro seznam položek v jiné než abecední pořadí, jako například obsahovat soubory nebo cesty v projektu.

[CComboBox](../mfc/reference/ccombobox-class.md)<br/>
Okno ovládacího prvku pole se seznamem. Pole se seznamem se skládá z ovládacího prvku pro úpravy plus pole se seznamem.

[CComboBoxEx](../mfc/reference/ccomboboxex-class.md)<br/>
Poskytnutím podpory pro seznamy obrázků rozšiřuje ovládací prvek pole se seznamem.

[Cchecklistbox –](../mfc/reference/cchecklistbox-class.md)<br/>
Zobrazí seznam položek pomocí zaškrtávacích políček, která uživatel může zaškrtněte nebo zrušte zaškrtnutí, vedle každé položky.

[CListCtrl](../mfc/reference/clistctrl-class.md)<br/>
Zobrazí kolekci položek, každá se skládá z ikony a jmenovku do pravého podokna podobným způsobem v Průzkumníku souborů.

[CTreeCtrl](../mfc/reference/ctreectrl-class.md)<br/>
Zobrazuje hierarchický seznam ikony a popisky, které jsou uspořádány do levého podokna podobným způsobem v Průzkumníku souborů.

## <a name="toolbars-and-status-bars"></a>Panely nástrojů a stavové řádky

[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)<br/>
Poskytuje funkce pro Windows nástrojů běžný ovládací prvek. Většina MFC programy používají [ctoolbar –](../mfc/reference/ctoolbar-class.md) místo této třídy.

[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)<br/>
Vodorovné okno obvykle rozdělena na dvě podokna, ve kterých může aplikace zobrazit informace o stavu. Většina MFC programy používají [cstatusbar –](../mfc/reference/cstatusbar-class.md) místo této třídy.

## <a name="miscellaneous-controls"></a>Různé ovládací prvky

[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)<br/>
Zobrazí jednoduché videoklipu.

[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)<br/>
Malého vyskakovacího okna, která zobrazuje jeden řádek textu popisujícího účel nástroje v aplikaci.

[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)<br/>
Podporuje ovládací prvek rozšířené úpravy nebo jednoduchý kalendáře rozhraní ovládacího prvku, který umožňuje uživateli zvolit konkrétní datum nebo čas.

[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)<br/>
Zobrazuje názvy (popisky sloupců).

[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)<br/>
Podporuje ovládací prvek rozhraní jednoduché kalendář, který umožňuje uživateli vybrat datum.

[CTabCtrl](../mfc/reference/ctabctrl-class.md)<br/>
Ovládací prvek karty, na které může uživatel kliknout, obdobná oddělovačů v poznámkovém bloku.

[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)<br/>
Umožňuje uživateli vytvořit klávesové kombinace kláves, které může uživatel stisknout k rychlému provádění akce.

[Clinkctrl –](../mfc/reference/clinkctrl-class.md)<br/>
Generuje text značkami a spouští příslušné aplikace, když uživatel klikne na odkaz vložený.

[Chtmleditctrl –](../mfc/reference/chtmleditctrl-class.md)<br/>
Poskytuje funkce pro ovládací prvek WebBrowser ActiveX v okně MFC.

## <a name="related-classes"></a>Související třídy

[Cimagelist –](../mfc/reference/cimagelist-class.md)<br/>
Poskytuje funkce pro seznam obrázků Windows. Seznamy obrázků se používají s ovládacími prvky seznam a stromu ovládacích prvků. Můžete také používají k ukládání a archivovat sadu rastrové obrázky stejné velikosti.

[Cctrlview –](../mfc/reference/cctrlview-class.md)<br/>
Základní třída pro všechna zobrazení související s ovládacími prvky Windows. Zobrazení založená na ovládací prvky jsou popsané níže.

[CEditView](../mfc/reference/ceditview-class.md)<br/>
Zobrazení, která obsahuje standardní Windows ovládacích prvků pro úpravy.

[Cricheditview –](../mfc/reference/cricheditview-class.md)<br/>
Zobrazení, které obsahuje Windows bohatých ovládacích prvků pro úpravy.

[CListView](../mfc/reference/clistview-class.md)<br/>
Zobrazení, která obsahuje ovládací prvek seznamu Windows.

[CTreeView](../mfc/reference/ctreeview-class.md)<br/>
Zobrazení, která obsahuje ovládací prvek stromu Windows.

## <a name="see-also"></a>Viz také

[Přehled tříd](../mfc/class-library-overview.md)


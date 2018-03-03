---
title: "Řízení třídy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 376fb3836d92a1fae348929a7faa49b44dfd866e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="control-classes"></a>Třídy ovládacích prvků
Třídy ovládacích prvků zapouzdřit širokou škálu od statický text ovládací prvky pro ovládací prvky stromů standardní ovládací prvky systému Windows. Kromě toho MFC nabízí některé nové ovládací prvky, včetně tlačítka s pruhy rastrové obrázky a řízení.  
  
 Ovládací prvky, jejichž názvy tříd končit "**Ctrl**" byly nové v systému Windows 95 a Windows NT verze 3.51.  
  
## <a name="static-display-controls"></a>Statické ovládací prvky zobrazení  
 [CStatic](../mfc/reference/cstatic-class.md)  
 Okno zobrazení statické. Statické ovládací prvky slouží k označení, pole nebo oddělení dalších ovládacích prvků v nebo dialogovém okně. Může také zobrazit grafické obrázky než text nebo pole.  
  
## <a name="text-controls"></a>Ovládacích prvků textu  
 [CEdit](../mfc/reference/cedit-class.md)  
 Okno s ovládací prvek upravovat text. Upravit ovládací prvky se používají tak, aby přijímal textový vstup od uživatele.  
  
 [CIPAddressCtrl](../mfc/reference/cipaddressctrl-class.md)  
 Podporuje textové pole pro manipulaci s adresu Internet Protocol (IP).  
  
 [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)  
 Ovládací prvek, ve kterém může uživatel zadat a upravit text. Na rozdíl od řízení zapouzdřené v `CEdit`, ovládacího prvku RichEdit podporuje znak a formátování odstavce a objekty OLE.  
  
## <a name="controls-that-represent-numbers"></a>Ovládací prvky, které představují čísla  
 [CSliderCtrl](../mfc/reference/csliderctrl-class.md)  
 Ovládací prvek obsahující jezdce, které uživatel přesune na vyberte hodnotu nebo sadu hodnot.  
  
 [CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)  
 Pár tlačítek uživatele můžete kliknout na zvýší nebo sníží hodnotu.  
  
 [CProgressCtrl](../mfc/reference/cprogressctrl-class.md)  
 Zobrazí obdélníku, která je zadána postupně zleva doprava informace o průběhu operace.  
  
 [CScrollBar](../mfc/reference/cscrollbar-class.md)  
 Okno pro řízení posuvníku. Třída poskytuje funkci posuvníku pro použití jako ovládacího prvku v dialogovém okně nebo okno, pomocí kterého může uživatel zadat pozici v rozsahu.  
  
## <a name="buttons"></a>Tlačítka  
 [CButton](../mfc/reference/cbutton-class.md)  
 Okno Ovládací prvek tlačítko. Třída poskytuje programovací rozhraní pro tlačítko, zaškrtněte políčko nebo přepínač v nebo dialogovém okně.  
  
 [CBitmapButton](../mfc/reference/cbitmapbutton-class.md)  
 Tlačítko rastrový obrázek než textový popisek.  
  
## <a name="lists"></a>Seznamy  
 [Clistbox –](../mfc/reference/clistbox-class.md)  
 Okno ovládacího prvku pole se seznamem. Zobrazuje seznam položek, které můžete zobrazit a vybrat uživatele.  
  
 [CDragListBox](../mfc/reference/cdraglistbox-class.md)  
 Poskytuje funkci Windows pole se seznamem; Umožňuje uživateli přesunout položky seznamu pole, jako jsou názvy souborů a řetězec literály, v rámci pole se seznamem. Seznamy díky této funkci jsou užitečné pro seznam položek v jiné než abecedním pořadí, jako například obsahovat názvy cest nebo soubory v projektu.  
  
 [CComboBox](../mfc/reference/ccombobox-class.md)  
 Okno ovládacího prvku pole se seznamem. Pole se seznamem se skládá z ovládacího prvku úprav plus pole se seznamem.  
  
 [CComboBoxEx](../mfc/reference/ccomboboxex-class.md)  
 Rozšiřuje ovládacího prvku pole se seznamem se tím, že poskytuje podporu pro seznamy obrázků.  
  
 [CCheckListBox](../mfc/reference/cchecklistbox-class.md)  
 Zobrazí seznam položek pomocí zaškrtávacích políček, které uživatel může zaškrtněte nebo zrušte zaškrtnutí, vedle jednotlivých položek.  
  
 [CListCtrl](../mfc/reference/clistctrl-class.md)  
 Zobrazí kolekce položek, každý se skládá z ikonu a štítku, v pravém podokně podobným způsobem v Průzkumníku souborů.  
  
 [CTreeCtrl](../mfc/reference/ctreectrl-class.md)  
 Zobrazí hierarchické seznam ikon a popisky uspořádané podobným způsobem, v levém podokně v Průzkumníku souborů.  
  
## <a name="toolbars-and-status-bars"></a>Panely nástrojů a stavové řádky  
 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)  
 Poskytuje funkci Windows běžné ovládací prvek panelu nástrojů. Většina MFC programy používají [ctoolbar –](../mfc/reference/ctoolbar-class.md) namísto této třídy.  
  
 [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)  
 Vodorovné okno obvykle rozdělené do podokna, ve kterých se aplikace můžete zobrazit informace o stavu. Většina MFC programy používají [cstatusbar –](../mfc/reference/cstatusbar-class.md) namísto této třídy.  
  
## <a name="miscellaneous-controls"></a>Ostatní ovládací prvky  
 [CAnimateCtrl](../mfc/reference/canimatectrl-class.md)  
 Zobrazí jednoduchý klip videa.  
  
 [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)  
 Malé místní okno, které zobrazuje jeden řádek textu popisující účel nástroj v aplikaci.  
  
 [CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)  
 Podporuje ovládacího prvku rozšířené úpravy nebo ovládacího prvku Kalendář jednoduché rozhraní, který umožňuje uživateli vybrat konkrétní datum nebo čas hodnotu.  
  
 [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)  
 Zobrazí názvy nebo popisky sloupců.  
  
 [CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)  
 Podporuje rozhraní ovládacího prvku jednoduché kalendář, který umožňuje uživateli vybrat datum.  
  
 [CTabCtrl](../mfc/reference/ctabctrl-class.md)  
 Ovládací prvek karty, na kterých uživatel může kliknout na, podobá oddělovačů v poznámkovém bloku.  
  
 [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)  
 Umožňuje uživateli vytvořit aktivní kombinaci kláves, které může uživatel stisknout rychle provedení akce.  
  
 [CLinkCtrl](../mfc/reference/clinkctrl-class.md)  
 Vykreslí text značkami a odpovídající aplikace spustí, když uživatel klikne na odkaz vložený.  
  
 [CHtmlEditCtrl](../mfc/reference/chtmleditctrl-class.md)  
 Poskytuje funkce ovládacího prvku WebBrowser ActiveX v okně knihovny MFC.  
  
## <a name="related-classes"></a>Související třídy  
 [CImageList](../mfc/reference/cimagelist-class.md)  
 Poskytuje funkci seznamu obrázků systému Windows. Seznamy obrázků se používají s ovládacími prvky seznam a ovládací prvky stromů. Můžete také používají k ukládání a archivaci sadu bitmap stejnou velikost.  
  
 [CCtrlView](../mfc/reference/cctrlview-class.md)  
 Základní třída pro všechna zobrazení související s ovládacími prvky systému Windows. Zobrazení založená na ovládací prvky jsou popsané níže.  
  
 [CEditView](../mfc/reference/ceditview-class.md)  
 Zobrazení, který obsahuje standardní Windows ovládacích prvků pro úpravy.  
  
 [Cricheditview –](../mfc/reference/cricheditview-class.md)  
 Zobrazení, který obsahuje bohatou Windows ovládacích prvků pro úpravy.  
  
 [CListView](../mfc/reference/clistview-class.md)  
 Zobrazení, které obsahuje seznam ovládacího prvku Windows.  
  
 [CTreeView](../mfc/reference/ctreeview-class.md)  
 Zobrazení, které obsahuje ovládacím prvkem strom systému Windows.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../mfc/class-library-overview.md)


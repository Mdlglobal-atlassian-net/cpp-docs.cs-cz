---
title: "TN014: Vlastní ovládací prvky | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.controls
dev_langs:
- C++
helpviewer_keywords:
- TN014
- custom controls [MFC]
ms.assetid: 1917a498-f643-457c-b570-9a0af7dbf7bb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b4ffc4f26ed365673cdfb525c2bf3653827cc4ba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="tn014-custom-controls"></a>TN014: Vlastní ovládací prvky
Tato poznámka popisuje Podpora MFC pro samoobslužné vykreslování a vlastní ovládací prvky. Také popisuje dynamické vytváření podtříd a popisuje vztah mezi [CWnd](../mfc/reference/cwnd-class.md) objekty a `HWND`s.  
  
 Ukázková aplikace MFC CTRLTEST znázorňuje, jak používat mnoho vlastní ovládací prvky. Najdete ve zdrojovém kódu pro ukázku MFC Obecné [CTRLTEST](../visual-cpp-samples.md) a online nápovědy.  
  
## <a name="owner-draw-controlsmenus"></a>Kreslení vlastníka ovládací prvky či nabídek  
 Windows poskytuje podporu pro vykreslování vlastníka ovládací prvky a nabídky pomocí zpráv systému Windows. Nadřazené okno Ovládací prvek nebo nabídky obdrží tyto zprávy a volání funkce v odpovědi. Tyto funkce můžete přizpůsobit vzhled a chování ovládacího prvku vykreslování vlastníka nebo nabídky můžete přepsat.  
  
 MFC přímo podporuje vykreslování vlastníka s následující funkce:  
  
- [CWnd::OnDrawItem](../mfc/reference/cwnd-class.md#ondrawitem)  
  
- [CWnd::OnMeasureItem](../mfc/reference/cwnd-class.md#onmeasureitem)  
  
- [CWnd::OnCompareItem](../mfc/reference/cwnd-class.md#oncompareitem)  
  
- [CWnd::OnDeleteItem](../mfc/reference/cwnd-class.md#ondeleteitem)  
  
 Můžete přepsat tyto funkce ve vašem `CWnd` odvozené třídy k implementaci vlastní kreslení chování.  
  
 Tento přístup nevede k opakovaně použitelný kód. Pokud máte dvou podobné ovládacích prvků ve dvou různých `CWnd` třídy, je nutné implementovat chování vlastního ovládacího prvku ve dvou umístěních. Tento problém řeší architektura podporované MFC samoobslužné vykreslování ovládacího prvku.  
  
## <a name="self-draw-controls-and-menus"></a>Samoobslužné vykreslení ovládacích prvků a nabídky  
 Poskytuje výchozí implementaci MFC (v `CWnd` a [cmenu –](../mfc/reference/cmenu-class.md) třídy) pro standardní vykreslování vlastníka zprávy. Tato výchozí implementace bude dekódování parametrů vykreslování vlastníka a delegovat vykreslování vlastníka zprávy pro ovládací prvky nebo nabídky. Tomu se říká samoobslužné kreslení protože kreslení kód je ve třídě ovládacího prvku nebo nabídky, ne v okně vlastníka.  
  
 Pomocí automatických vykreslení ovládacích prvků můžete vytvořit opakovaně použitelný ovládací prvek třídy, které používají sémantiku vykreslování vlastníka k zobrazení ovládacího prvku. Kód pro vykreslení ovládacího prvku je ve třídě ovládacího prvku, ne jeho nadřazený objekt. Toto je objektově orientované přístup k programování vlastního ovládacího prvku. Přidejte následující seznam funkcí samoobslužné kreslení třídy:  
  
-   Pro samoobslužné kreslení tlačítka:  
  
 ```  
    CButton:DrawItem(LPDRAWITEMSTRUCT);
*// insert code to draw this button  
 ```  
  
-   Pro samoobslužné kreslení nabídky:  
  
 ```  
    CMenu:MeasureItem(LPMEASUREITEMSTRUCT);
*// insert code to measure the size of an item in this menu  
    CMenu:DrawItem(LPDRAWITEMSTRUCT);
*// insert code to draw an item in this menu  
 ```  
  
-   U polí s samoobslužné kreslení seznamu:  
  
 ```  
    CListBox:MeasureItem(LPMEASUREITEMSTRUCT);
*// insert code to measure the size of an item in this list box  
    CListBox:DrawItem(LPDRAWITEMSTRUCT);
*// insert code to draw an item in this list box  
 
    CListBox:CompareItem(LPCOMPAREITEMSTRUCT);
*// insert code to compare two items in this list box if LBS_SORT  
    CListBox:DeleteItem(LPDELETEITEMSTRUCT);
*// insert code to delete an item from this list box  
 ```  
  
-   Pro samoobslužné kreslení pole se seznamem:  
  
 ```  
    CComboBox:MeasureItem(LPMEASUREITEMSTRUCT);
*// insert code to measure the size of an item in this combo box  
    CComboBox:DrawItem(LPDRAWITEMSTRUCT);
*// insert code to draw an item in this combo box  
 
    CComboBox:CompareItem(LPCOMPAREITEMSTRUCT);
*// insert code to compare two items in this combo box if CBS_SORT  
    CComboBox:DeleteItem(LPDELETEITEMSTRUCT);
*// insert code to delete an item from this combo box  
 ```  
  
 Podrobnosti o vykreslování vlastníka struktury ([drawitemstruct –](../mfc/reference/drawitemstruct-structure.md), [measureitemstruct –](../mfc/reference/measureitemstruct-structure.md), [compareitemstruct –](../mfc/reference/compareitemstruct-structure.md), a [deleteitemstruct –](../mfc/reference/deleteitemstruct-structure.md)) najdete v dokumentaci MFC pro `CWnd::OnDrawItem`, `CWnd::OnMeasureItem`, `CWnd::OnCompareItem`, a `CWnd::OnDeleteItem` v uvedeném pořadí.  
  
## <a name="using-self-draw-controls-and-menus"></a>Pomocí automatických vykreslení ovládacích prvků a nabídky  
 Pro samoobslužné kreslení nabídky, je nutné přepsat i `OnMeasureItem` a `OnDrawItem` metody.  
  
 Pro samoobslužné kreslení seznamy a pole se seznamem, je nutné přepsat `OnMeasureItem` a `OnDrawItem`. Je nutné zadat `LBS_OWNERDRAWVARIABLE` styl seznamy nebo `CBS_OWNERDRAWVARIABLE` styl pro pole se seznamem oknech v šablony dialogového okna. `OWNERDRAWFIXED` Styl nebude fungovat s samoobslužné kreslení položky, protože výška pevné položka je určen před svým vykreslení ovládacích prvků, které jsou připojené k pole se seznamem. (Můžete použít metody [CListBox::SetItemHeight](../mfc/reference/clistbox-class.md#setitemheight) a [CComboBox::SetItemHeight](../mfc/reference/ccombobox-class.md#setitemheight) k překonání tohoto omezení.)  
  
 Přepnutí do `OWNERDRAWVARIABLE` styl vynutí systému pro použití `NOINTEGRALHEIGHT` styl do ovládacího prvku. Protože ovládacího prvku nelze vypočítat integrální výšky s proměnnou velikost položky, výchozí styl `INTEGRALHEIGHT` je ignorován a ovládací prvek je vždy `NOINTEGRALHEIGHT`. Pokud své položky jsou pevnou výšku, můžete zabránit částečné položky přitahuje zadáním na velikost ovládacího prvku celé číslo násobitel velikosti položky.  
  
 Pro samoobslužné kreslení seznamy a pole se seznamem s `LBS_SORT` nebo `CBS_SORT` styl, je nutné přepsat `OnCompareItem` metoda.  
  
 Pro samoobslužné kreslení seznamy a pole se seznamem, `OnDeleteItem` není obvykle přepsána. Můžete přepsat `OnDeleteItem` Pokud chcete provést žádné speciální zpracování. Jeden případ, kde bude příslušné je při další paměti nebo jiných prostředků se ukládají s každou položku seznamu pole nebo pole se seznamem pole.  
  
## <a name="examples-of-self-drawing-controls-and-menus"></a>Příkladem samoobslužné vykreslování ovládacích prvků a nabídky  
 Ukázka MFC Obecné [CTRLTEST](../visual-cpp-samples.md) poskytuje ukázky, samoobslužných kreslení nabídky a pole se seznamem samoobslužné kreslení.  
  
 Nejobvyklejším příkladem samoobslužné kreslení tlačítko je tlačítko rastrového obrázku. Tlačítko rastrového obrázku je tlačítko, které zobrazuje jeden, dva nebo tři rastrové obrázky jako různých stavů. Příkladem je součástí třídy MFC [CBitmapButton](../mfc/reference/cbitmapbutton-class.md).  
  
## <a name="dynamic-subclassing"></a>Dynamické vytváření podtříd  
 Někdy budete chtít změnit funkce objekt, který již existuje. V předchozích příkladech je nutné přizpůsobit ovládacích prvků, než byly vytvořeny. Dynamické vytváření podtříd umožňuje přizpůsobit ovládací prvek, který již existuje.  
  
 Vytváření podtříd je termín Windows k nahrazení [WndProc](http://msdn.microsoft.com/en-us/94ba8ffa-3c36-46d4-ac74-9bd10b1ffd26) okna s přizpůsobeným `WndProc` a volání starý `WndProc` pro výchozí funkce.  
  
 Tento model nelze zaměňovat s odvození třídy C++. Informace, podmínky C++ *základní třída* a *odvozené třídy* se podobá *supertřídě* a *podtřídami* v systému Windows objekt modelu. Odvození C++ s vytváření podtříd MFC a Windows jsou funkčně podobné, s výjimkou C++ nepodporuje dynamické vytváření podtříd.  
  
 `CWnd` Třída poskytuje připojení mezi objekt C++ (odvozený z `CWnd`) a objektem okna v systému Windows (označované jako `HWND`).  
  
 Existují tři běžné způsoby, které se týkají:  
  
- `CWnd`vytvoří `HWND`. Můžete změnit chování v odvozené třídě vytvořením třídy odvozené od `CWnd`. `HWND` Se vytvoří, když aplikace volá [CWnd::Create](../mfc/reference/cwnd-class.md#create).  
  
-   Aplikace připojí `CWnd` na stávající `HWND`. Chování existující okna se nemění. Toto je případ delegování a je možné díky volání [CWnd::Attach](../mfc/reference/cwnd-class.md#attach) alias stávající `HWND` k `CWnd` objektu.  
  
- `CWnd`je připojena k existující `HWND` a můžete změnit chování v odvozené třídě. Tomu se říká dynamické vytvoření podtřídy, protože jsme se změna chování a proto třídu objektu systému Windows v době běhu.  
  
 Dynamické vytváření podtříd můžete dosáhnout pomocí metody [CWnd::SubclassWindow](../mfc/reference/cwnd-class.md#subclasswindow) a[CWnd::SubclassDlgItem](../mfc/reference/cwnd-class.md#subclassdlgitem).  
  
 Připojte oba rutiny `CWnd` objekt, který má na existující `HWND`. `SubclassWindow`provede `HWND` přímo. `SubclassDlgItem`je pomocné funkce, která přebírá ID ovládacího prvku a nadřazeného okna. `SubclassDlgItem`je určený pro připojení objekty C++ pro ovládací prvky dialogového okna, které jsou vytvořené z šablony dialogového okna.  
  
 Najdete v článku [CTRLTEST](../visual-cpp-samples.md) příklad několik příkladů použití `SubclassWindow` a `SubclassDlgItem`.  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)


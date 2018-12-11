---
title: 'TN014: Vlastní ovládací prvky'
ms.date: 06/28/2018
f1_keywords:
- vc.controls
helpviewer_keywords:
- TN014
- custom controls [MFC]
ms.assetid: 1917a498-f643-457c-b570-9a0af7dbf7bb
ms.openlocfilehash: 1f04029e47ee7d262cdc5e2eab463799acd7d943
ms.sourcegitcommit: 975098222db3e8b297607cecaa1f504570a11799
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53178405"
---
# <a name="tn014-custom-controls"></a>TN014: Vlastní ovládací prvky

Tato poznámka popisuje podporu knihovny MFC pro vlastní vykreslování a vlastní ovládací prvky. Také popisuje dynamické vytváření podtříd a popisuje vztah mezi [CWnd](../mfc/reference/cwnd-class.md) objekty a `HWND`s.

Ukázkové aplikace knihovny MFC CTRLTEST ukazuje, jak použít mnoho vlastních ovládacích prvků. Zobrazit zdrojový kód ukázkové MFC Obecné [CTRLTEST](../visual-cpp-samples.md) a online nápovědy.

## <a name="owner-draw-controlsmenus"></a>Owner Draw ovládacích prvků či nabídek

Windows poskytuje podporu pro ovládací prvky vykreslené vlastníkem a nabídek s použitím zpráv Windows. Nadřazené okno ovládacího prvku nebo nabídky obdrží tyto zprávy a volání funkce v odpovědi. Můžete přepsat tyto funkce přizpůsobit vzhled a chování ovládacím prvku vykresleném vlastníkem nebo nabídky.

Knihovna MFC přímo podporuje vykreslené vlastníkem s následující funkce:

- [CWnd::OnDrawItem](../mfc/reference/cwnd-class.md#ondrawitem)

- [CWnd::OnMeasureItem](../mfc/reference/cwnd-class.md#onmeasureitem)

- [CWnd::OnCompareItem](../mfc/reference/cwnd-class.md#oncompareitem)

- [CWnd::OnDeleteItem](../mfc/reference/cwnd-class.md#ondeleteitem)

Můžete přepsat tyto funkce ve vaší `CWnd` odvozené třídy k implementaci vlastních draw chování.

Tento přístup nenastane opakovaně použitelný kód. Pokud máte dvě podobné ovládací prvky ve dvou různých `CWnd` třídy, je nutné implementovat vlastní ovládací prvek chování ve dvou umístěních. Tento problém řeší architektura knihovny MFC podporována vlastní vykreslení ovládacího prvku.

## <a name="self-draw-controls-and-menus"></a>Vlastní vykreslení ovládacích prvků a v nabídkách

Knihovna MFC poskytuje výchozí implementaci (v `CWnd` a [cmenu –](../mfc/reference/cmenu-class.md) třídy) pro standardní vykreslené vlastníkem zprávy. Tato výchozí implementace bude dekódovat vykreslené vlastníkem. parametry a delegovat vykreslené vlastníkem zprávy, které mají ovládací prvky nebo nabídce. Tomu se říká samostatně nakreslit protože kreslení kód je ve třídě ovládacího prvku nebo nabídky není v nadřazenému oknu.

S použitím vlastní vykreslení ovládacích prvků můžete vytvářet opakovaně použitelné ovládací prvek třídy, které používají sémantiku vykreslené vlastníkem. Chcete-li zobrazit ovládací prvek. Kód pro vykreslení ovládacího prvku je ve třídě ovládacího prvku, nikoli jeho nadřazený objekt. Toto je metodiky objektově orientované programování vlastního ovládacího prvku. Přidejte do třídy samostatně nakreslit následující seznam funkcí:

- Pro vlastní vykreslení tlačítka:

    ```cpp
    CButton:DrawItem(LPDRAWITEMSTRUCT);
    // insert code to draw this button
    ```

- Pro vlastní vykreslení nabídky:

    ```cpp
    CMenu:MeasureItem(LPMEASUREITEMSTRUCT);
    // insert code to measure the size of an item in this menu
    CMenu:DrawItem(LPDRAWITEMSTRUCT);
    // insert code to draw an item in this menu
    ```

- Pro pole se seznamem samostatně nakreslit:

    ```cpp
    CListBox:MeasureItem(LPMEASUREITEMSTRUCT);
    // insert code to measure the size of an item in this list box
    CListBox:DrawItem(LPDRAWITEMSTRUCT);
    // insert code to draw an item in this list box

    CListBox:CompareItem(LPCOMPAREITEMSTRUCT);
    // insert code to compare two items in this list box if LBS_SORT
    CListBox:DeleteItem(LPDELETEITEMSTRUCT);
    // insert code to delete an item from this list box
    ```

- Pro vlastní vykreslení pole se seznamem:

    ```cpp
    CComboBox:MeasureItem(LPMEASUREITEMSTRUCT);
    // insert code to measure the size of an item in this combo box
    CComboBox:DrawItem(LPDRAWITEMSTRUCT);
    // insert code to draw an item in this combo box

    CComboBox:CompareItem(LPCOMPAREITEMSTRUCT);
    // insert code to compare two items in this combo box if CBS_SORT
    CComboBox:DeleteItem(LPDELETEITEMSTRUCT);
    // insert code to delete an item from this combo box
    ```

Další informace o strukturách vykreslené vlastníkem. ([drawitemstruct –](/windows/desktop/api/winuser/ns-winuser-tagdrawitemstruct), [measureitemstruct –](/windows/desktop/api/winuser/ns-winuser-tagmeasureitemstruct), [compareitemstruct –](/windows/desktop/api/winuser/ns-winuser-tagcompareitemstruct), a [deleteitemstruct –](/windows/desktop/api/winuser/ns-winuser-tagdeleteitemstruct)) najdete v dokumentaci knihovny MFC pro `CWnd::OnDrawItem`, `CWnd::OnMeasureItem`, `CWnd::OnCompareItem`, a `CWnd::OnDeleteItem` v uvedeném pořadí.

## <a name="using-self-draw-controls-and-menus"></a>Pomocí nabídky a místním vykreslení ovládacích prvků

Pro nabídky svým kreslení, je nutné přepsat i `OnMeasureItem` a `OnDrawItem` metody.

Samostatně nakreslit seznamy a pole se seznamem, je nutné přepsat `OnMeasureItem` a `OnDrawItem`. V šabloně dialogu je nutné zadat LBS_OWNERDRAWVARIABLE styl pro pole se seznamem nebo CBS_OWNERDRAWVARIABLE pro pole se seznamem. Styl OWNERDRAWFIXED nebude fungovat s místním kreslit položky, protože výšku položky pevné závisí před svým nakreslete ovládací prvky jsou připojeny k seznamu. (Můžete použít metody [CListBox::SetItemHeight](../mfc/reference/clistbox-class.md#setitemheight) a [CComboBox::SetItemHeight](../mfc/reference/ccombobox-class.md#setitemheight) k překonání tohoto omezení.)

Přepnutí do stylu OWNERDRAWVARIABLE vynutí systém stylu NOINTEGRALHEIGHT na ovládacím prvku. Vzhledem k tomu, že ovládací prvek nelze vypočítat integrální výška s proměnnou velikostí položek, se ignoruje výchozí styl INTEGRALHEIGHT a ovládacího prvku je vždy NOINTEGRALHEIGHT. Pokud vaše položky jsou pevné výšky, můžete zabránit částečných položek ve které je cílem vykreslování tak, že určíte velikost ovládacího prvku celé číslo multiplikátor velikosti položky.

Pro vytvoření vlastní pole se seznamem a pole se seznamem se stylem LBS_SORT nebo CBS_SORT, je nutné přepsat `OnCompareItem` metody.

Pro vlastní kreslení seznamy a pole se seznamem, `OnDeleteItem` není obvykle přepsána. Můžete přepsat `OnDeleteItem` Pokud chcete provést všechna speciální zpracování. Jeden případ, ve kterém jde použít při další paměť nebo další prostředky se ukládají s každou položku seznamu nebo pole se seznamem pole.

## <a name="examples-of-self-drawing-controls-and-menus"></a>Příkladem samoobslužné vykreslení ovládacích prvků a v nabídkách

Ukázky knihovny MFC Obecné [CTRLTEST](../visual-cpp-samples.md) obsahuje ukázky nabídky svým kreslení a místním vykreslení seznamu.

Většina Typickým příkladem samoobslužné výkresu tlačítko je tlačítko rastrového obrázku. Rastrový obrázek tlačítko je tlačítko, které zobrazuje jeden, dva nebo tři bitmapové obrázky pro různé stavy. Příkladem je součástí třídy knihovny MFC [cbitmapbutton –](../mfc/reference/cbitmapbutton-class.md).

## <a name="dynamic-subclassing"></a>Dynamické vytváření podtříd

Někdy budete chtít změnit funkce objektu, který již existuje. V předchozích příkladech je nutné k přizpůsobení ovládacích prvků, než byly vytvořeny. Dynamické vytváření podtříd umožňuje přizpůsobit ovládací prvek, který již byl vytvořen.

Vytváření podtříd je termín Windows pro nahrazení <xref:System.Windows.Forms.Control.WndProc%2A> okna s přizpůsobeným `WndProc` a volání starého `WndProc` pro výchozí funkce.

To třeba nezaměňovat s odvození třídy jazyka C++. Pro objasnění, podmínky C++ *základní třída* a *odvozené třídy* jsou podobná *supertřídě* a *podtřídy* v Windows objektový model. Odvození C++ s vytváření podtříd knihovny MFC a Windows jsou funkčně podobné, s výjimkou C++ nepodporuje dynamické vytváření podtříd.

`CWnd` Třída poskytuje připojení mezi objekt jazyka C++ (odvozený od `CWnd`) a objekt okna Windows (označované jako `HWND`).

Existují tři běžné způsoby, které se týkají:

- `CWnd` vytvoří `HWND`. Můžete změnit chování v odvozené třídě tak, že vytvoříte třídu odvozenou z `CWnd`. `HWND` Se vytvoří, když vaše aplikace volá [CWnd::Create](../mfc/reference/cwnd-class.md#create).

- Připojí aplikace `CWnd` do existujícího `HWND`. Chování stávajícím okně se nezmění. To se stává delegování a je možné díky volání [CWnd::Attach](../mfc/reference/cwnd-class.md#attach) na alias z existujícího `HWND` k `CWnd` objektu.

- `CWnd` je připojen k existujícímu `HWND` a můžete změnit chování v odvozené třídě. Tomu se říká dynamické vytvoření podtřídy, protože jsme se mění chování a proto třídu Windows objektu v době běhu.

Dynamické vytváření podtříd lze dosáhnout pomocí metod [CWnd::SubclassWindow](../mfc/reference/cwnd-class.md#subclasswindow) a[CWnd::SubclassDlgItem](../mfc/reference/cwnd-class.md#subclassdlgitem).

Obě rutiny připojit `CWnd` objektu do existujícího `HWND`. `SubclassWindow` přijímá `HWND` přímo. `SubclassDlgItem` je pomocná funkce, která přijímá ID ovládacího prvku a nadřazeného okna. `SubclassDlgItem` je určená pro objekty C++ se připojuje k ovládací prvky dialogového okna, které jsou vytvořené ze šablony dialogového okna.

Zobrazit [CTRLTEST](../visual-cpp-samples.md) příklad pro několik příkladů použití `SubclassWindow` a `SubclassDlgItem`.

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

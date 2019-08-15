---
title: 'TN014: Vlastní ovládací prvky'
ms.date: 06/28/2018
f1_keywords:
- vc.controls
helpviewer_keywords:
- TN014
- custom controls [MFC]
ms.assetid: 1917a498-f643-457c-b570-9a0af7dbf7bb
ms.openlocfilehash: 2960c5b8585519adb535e5611315ec4ececcf53e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511184"
---
# <a name="tn014-custom-controls"></a>TN014: Vlastní ovládací prvky

Tato poznámka popisuje podporu knihovny MFC pro vlastní ovládací prvky a ovládací prvky pro vlastní vykreslení. Popisuje také dynamické podtřídy a popisuje vztah mezi objekty [CWnd](../mfc/reference/cwnd-class.md) a `HWND`s.

Ukázková aplikace MFC CTRLTEST ukazuje, jak použít mnoho vlastních ovládacích prvků. Podívejte se na zdrojový kód pro knihovnu MFC General Sample [CTRLTEST](../overview/visual-cpp-samples.md) a online nápovědu.

## <a name="owner-draw-controlsmenus"></a>Ovládací prvky nebo nabídky pro vykreslování vlastníka

Systém Windows poskytuje podporu pro ovládací prvky a nabídky pro kreslení vlastníka pomocí zpráv systému Windows. Nadřazené okno libovolného ovládacího prvku nebo nabídky obdrží tyto zprávy a volání funkcí v reakci. Tyto funkce můžete přepsat, chcete-li přizpůsobit vizuální vzhled a chování ovládacího prvku nebo nabídky vykresleného vlastníkem.

MFC přímo podporuje vlastní vykreslování pomocí následujících funkcí:

- [CWnd:: OnDrawItem](../mfc/reference/cwnd-class.md#ondrawitem)

- [CWnd:: OnMeasureItem](../mfc/reference/cwnd-class.md#onmeasureitem)

- [CWnd:: OnCompareItem](../mfc/reference/cwnd-class.md#oncompareitem)

- [CWnd::OnDeleteItem](../mfc/reference/cwnd-class.md#ondeleteitem)

Tyto funkce můžete přepsat v `CWnd` odvozené třídě pro implementaci vlastního chování vykreslování.

Tento přístup nevede k opakovanému použití kódu. Pokud máte dva podobné ovládací prvky ve dvou různých `CWnd` třídách, je nutné implementovat chování vlastního ovládacího prvku ve dvou umístěních. Architektura ovládacího prvku pro samoobslužné vykreslování, který je podporován knihovnou MFC, tento problém vyřeší.

## <a name="self-draw-controls-and-menus"></a>Ovládací prvky a nabídky pro samoobslužné kreslení

Knihovna MFC poskytuje výchozí implementaci (v `CWnd` třídách [CMenu –](../mfc/reference/cmenu-class.md) a) pro zprávy standardního vykreslování vlastníka. Tato výchozí implementace dekóduje parametry vykreslování vlastníka a deleguje zprávy nakreslené vlastníkem v ovládacích prvcích nebo nabídce. Tato funkce se nazývá sebe Draw, protože kód kresby je ve třídě ovládacího prvku nebo nabídky, nikoli v nadřazeném okně.

Pomocí ovládacích prvků pro vlastní vykreslování můžete vytvořit opakovaně použitelné třídy ovládacích prvků, které používají sémantiku vykreslování vlastníka k zobrazení ovládacího prvku. Kód pro vykreslení ovládacího prvku je součástí třídy ovládacího prvku, nikoli jeho nadřazeného objektu. Jedná se o objektově orientovaný přístup k programování vlastního ovládacího prvku. Přidejte následující seznam funkcí do tříd vlastního vykreslování:

- Pro tlačítka pro vnitřní vykreslování:

    ```cpp
    CButton:DrawItem(LPDRAWITEMSTRUCT);
    // insert code to draw this button
    ```

- Pro nabídky pro samoobslužné kreslení:

    ```cpp
    CMenu:MeasureItem(LPMEASUREITEMSTRUCT);
    // insert code to measure the size of an item in this menu
    CMenu:DrawItem(LPDRAWITEMSTRUCT);
    // insert code to draw an item in this menu
    ```

- Pro pole se seznamem automatického vykreslování:

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

- Pro pole se seznamem automatického vykreslování:

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

Podrobnosti o strukturách vykreslování vlastníka ([DRAWITEMSTRUCT –](/windows/win32/api/winuser/ns-winuser-drawitemstruct), [MEASUREITEMSTRUCT –](/windows/win32/api/winuser/ns-winuser-measureitemstruct), [COMPAREITEMSTRUCT –](/windows/win32/api/winuser/ns-winuser-compareitemstruct)a [DELETEITEMSTRUCT –](/windows/win32/api/winuser/ns-winuser-deleteitemstruct)) naleznete v dokumentaci knihovny MFC `CWnd::OnDrawItem`pro, `CWnd::OnMeasureItem`, `CWnd::OnCompareItem`a `CWnd::OnDeleteItem` v uvedeném pořadí.

## <a name="using-self-draw-controls-and-menus"></a>Použití ovládacích prvků a nabídek pro samoobslužné kreslení

Pro nabídky, které mají samy sebe nakreslit, je `OnMeasureItem` nutné `OnDrawItem` přepsat metody a.

Pro pole seznamu a pole se seznamem musíte přepsat `OnMeasureItem` a. `OnDrawItem` Pro pole se seznamem v šabloně dialogového okna je nutné zadat styl LBS_OWNERDRAWVARIABLE pro seznamy nebo CBS_OWNERDRAWVARIABLE styl. Styl OWNERDRAWFIXED nebude fungovat s položkami, které se automaticky kreslí, protože je určena výška pevné položky před tím, než jsou ovládací prvky přichycené do seznamu připojeny k poli. (K překonání tohoto omezení můžete použít metody [CListBox –:: SetItemHeight](../mfc/reference/clistbox-class.md#setitemheight) a [CComboBox –:: SetItemHeight](../mfc/reference/ccombobox-class.md#setitemheight) .)

Přepnutí na styl OWNERDRAWVARIABLE vynutí, aby systém při použití stylu NOINTEGRALHEIGHT na ovládací prvek. Vzhledem k tomu, že ovládací prvek nemůže vypočítat integrální výšku s proměnlivou velikostí položek, je výchozí styl INTEGRALHEIGHT ignorován a ovládací prvek je vždy NOINTEGRALHEIGHT. Pokud jsou položky pevné výšky, můžete zabránit vykreslení částečných položek zadáním velikosti ovládacího prvku pro celočíselnou násobitel velikosti položky.

Pro samoobslužné seznamy a pole se seznamem se stylem LBS_SORT nebo CBS_SORT je nutné přepsat `OnCompareItem` metodu.

Pro samoobslužné seznamy a pole se seznamem `OnDeleteItem` není obvykle přepsána. Můžete přepsat `OnDeleteItem` , pokud chcete provést jakékoli speciální zpracování. Jeden případ, ve kterém by se to týká, je případ, kdy se do každého pole seznamu nebo položky pole se seznamem uloží další paměť nebo jiné prostředky.

## <a name="examples-of-self-drawing-controls-and-menus"></a>Příklady ovládacích prvků a nabídek pro samoobslužné kreslení

Knihovna MFC General Sample [CTRLTEST](../overview/visual-cpp-samples.md) poskytuje ukázky pro nabídku, která slouží k samostatnému vykreslení, a seznam automatického vykreslování.

Typickým příkladem tlačítka pro samoobslužné kreslení je rastrové tlačítko. Tlačítko rastrového obrázku je tlačítko, které zobrazuje jednu, dvě nebo tři rastrové obrázky pro různé stavy. Příklad je k dispozici v knihovně MFC třídy [CBitmapButton](../mfc/reference/cbitmapbutton-class.md).

## <a name="dynamic-subclassing"></a>Dynamické roztřídění

Občas budete chtít změnit funkčnost objektu, který již existuje. Předchozí příklady vyžadují, abyste ovládací prvky přizpůsobili před jejich vytvořením. Dynamické podtřídy umožňují přizpůsobit ovládací prvek, který již byl vytvořen.

Roztřídění je termín Windows pro nahrazení <xref:System.Windows.Forms.Control.WndProc%2A> okna vlastním přizpůsobeným `WndProc` a voláním starého `WndProc` pro výchozí funkce.

Nemělo by se zaměňovat s C++ odvozením třídy. Pro objasnění C++ *základní třídy* terms a *odvozené třídy* jsou obdobou na *supertřída* a podtřídu v modelu objektu Windows. C++odvození s využitím podtříd MFC a prostředí Windows je funkčně podobné, C++ s výjimkou dynamického podtříd.

Třída poskytuje připojení mezi C++ objektem (odvozeným od `CWnd`) a objektem okna `HWND`systému Windows (známé jako). `CWnd`

Existují tři běžné způsoby, které jsou v relaci:

- `CWnd``HWND`vytvoří. Chování v odvozené třídě lze upravit vytvořením třídy odvozené z `CWnd`. Je `HWND` vytvořena, když vaše aplikace volá [CWnd:: Create](../mfc/reference/cwnd-class.md#create).

- Aplikace připojí `CWnd` k existujícímu `HWND`. Chování stávajícího okna se nezmění. Jedná se o případ delegování a je možné ho volat pomocí metody [CWnd:: Attach](../mfc/reference/cwnd-class.md#attach) alias existujícího `HWND` `CWnd` objektu.

- `CWnd`je připojen k existujícímu `HWND` a lze upravit chování v odvozené třídě. Tento postup se nazývá dynamické podtříd, protože měníme chování, a proto třídu objektu Windows v době běhu.

Dynamické podtříd lze dosáhnout pomocí metod [CWnd:: SubclassWindow](../mfc/reference/cwnd-class.md#subclasswindow) a[CWnd:: SubclassDlgItem](../mfc/reference/cwnd-class.md#subclassdlgitem).

Obě rutiny připojí `CWnd` objekt k existujícímu `HWND`. `SubclassWindow``HWND` provede přímo. `SubclassDlgItem`je pomocná funkce, která přebírá ID ovládacího prvku a nadřazené okno. `SubclassDlgItem`je určen pro připojení C++ objektů k ovládacím prvkům vytvořeným ze šablony dialogového okna.

V příkladu [CTRLTEST](../overview/visual-cpp-samples.md) naleznete několik příkladů, kdy použít `SubclassWindow` a. `SubclassDlgItem`

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

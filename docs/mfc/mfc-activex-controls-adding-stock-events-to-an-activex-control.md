---
title: 'MFC – ovládací prvky ActiveX: Přidání uložených událostí do ovládacího prvku ActiveX'
ms.date: 11/04/2016
f1_keywords:
- EVENT__STOCK_ERROR
- EVENT__STOCK_READYSTATECHANGE
- ReadyStateChange
- EVENT__STOCK_MOUSEMOVE
- EVENT__STOCK_MOUSEUP
- EVENT__STOCK_DBLCLICK
- KeyPress
- EVENT__STOCK_KEYDOWN
- EVENT__STOCK
- EVENT__STOCK_MOUSEDOWN
- EVENT__STOCK_KEYPRESS
- EVENT__STOCK_CLICK
- EVENT__STOCK_KEYUP
helpviewer_keywords:
- MFC ActiveX controls [MFC], events
- KeyPress event
- FireDblClick event
- FireMouseDown event
- events [MFC], stock
- FireKeyPress event
- EVENT_STOCK_MOUSEMOVE event
- EVENT_STOCK_CLICK event
- FireClick event
- FireKeyUp event
- FireMouseUp event
- EVENT_STOCK_ERROREVENT event
- EVENT_STOCK_KEYDOWN event
- EVENT_STOCK_MOUSEDOWN event
- EVENT_STOCK_KEYPRESS macro [MFC]
- EVENT_STOCK_KEYUP event
- EVENT_STOCK_DBLCLICK event
- FireError event
- FireKeyDown event
- ReadyStateChange event
- EVENT_STOCK_MOUSEUP event
- FireMouseMove event
- EVENT_STOCK prefix
- EVENT_STOCK_READYSTATECHANGE event
- EVENT_STOCK_KEYPRESS event
ms.assetid: 3eeadc67-4b3d-4444-8caa-53054073988a
ms.openlocfilehash: 79cd4fc572e55c67cc5a2cfe3a00e04f2a4a7850
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364691"
---
# <a name="mfc-activex-controls-adding-stock-events-to-an-activex-control"></a>MFC – ovládací prvky ActiveX: Přidání uložených událostí do ovládacího prvku ActiveX

Události zásob se liší od vlastních událostí v tom, že jsou automaticky aktivovány třídou [COleControl](../mfc/reference/colecontrol-class.md). `COleControl`obsahuje předdefinované členské funkce, které vypalují události vyplývající z běžných akcí. Některé běžné akce `COleControl` implementované pomocí zahrnují jedno kliknutí a poklepání na ovládací prvek, události klávesnice a změny stavu tlačítek myši. Položkám mapy událostí pro skladové události vždy předchází předpona EVENT_STOCK.

## <a name="stock-events-supported-by-the-add-event-wizard"></a><a name="_core_stock_events_supported_by_classwizard"></a>Události na skladě podporované Průvodcem přidáním události

Třída `COleControl` poskytuje deset skladových událostí uvedených v následující tabulce. Chcete-li zadat události, které chcete mít v ovládacím prvku, pomocí [Průvodce přidáním události](../ide/add-event-wizard.md).

### <a name="stock-events"></a>Akciové akce

|Událost|Funkce vypalování|Komentáře|
|-----------|---------------------|--------------|
|Klikněte na|**void FireClick( )**|Aktivována při ovládacíprvek zachytí myš, všechny **BUTTONUP** (vlevo, uprostřed nebo vpravo) zpráva je přijata a tlačítko je uvolněna nad ovládacím prvkem. Stock MouseDown a MouseUp události dojít před touto událostí.<br /><br /> Záznam mapy událostí: **EVENT_STOCK_CLICK( )**|
|Tlačítko DblClick|**void FireDblClick( )**|Podobně jako Click, ale aktivována při přijetí zprávy **BUTTONDBLCLK.**<br /><br /> Záznam mapy událostí: **EVENT_STOCK_DBLCLICK( )**|
|Chyba|**void FireError( SCODE***scode* **, LPCSTR** `lpszDescription` , **UINT**`nHelpID`**= 0 )**        |Aktivuje se, když dojde k chybě v ovládacím prvku ActiveX mimo rozsah volání metody nebo přístupu k vlastnostem.<br /><br /> Záznam mapy událostí: **EVENT_STOCK_ERROREVENT( )**|
|Keydown|**void FireKeyDown( krátké** `nChar` **, krátké**`nShiftState`**)**      |Aktivováno `WM_SYSKEYDOWN` při `WM_KEYDOWN` přijetí zprávy nebo.<br /><br /> Záznam mapy událostí: **EVENT_STOCK_KEYDOWN( )**|
|Keypress|**void FireKeyPress( krátký** <strong>\*</strong> `pnChar` **)**    |Aktivováno `WM_CHAR` při přijetí zprávy.<br /><br /> Záznam mapy událostí: **EVENT_STOCK_KEYPRESS( )**|
|Keyup|**void FireKeyUp( krátké,** `nChar` **krátké**`nShiftState`**)**      |Aktivováno `WM_SYSKEYUP` při `WM_KEYUP` přijetí zprávy nebo.<br /><br /> Záznam mapy událostí: **EVENT_STOCK_KEYUP( )**|
|Mousedown|**void FireMouseDown(** `nButton` **krátké, krátké,** `nShiftState` **plovák***x* , **float***y***)**          |Aktivováno, pokud je přijata některá **BUTTONDOWN** (vlevo, uprostřed nebo vpravo). Myš je zachycena bezprostředně před tuto událost je aktivována.<br /><br /> Záznam mapy událostí: **EVENT_STOCK_MOUSEDOWN( )**|
|Mousemove|**void FireMouseMove(** `nButton` **krátké, krátké,** `nShiftState` **plovák***x* , **plovák***y***)**          |Aktivováno při přijetí WM_MOUSEMOVE zprávy.<br /><br /> Záznam mapy událostí: **EVENT_STOCK_MOUSEMOVE( )**|
|Mouseup|**void FireMouseUp(** `nButton` **krátké, krátké,** `nShiftState` **plovák***x* , **float***y***)**          |Je aktivována, pokud je přijata některá **BUTTONUP** (vlevo, uprostřed nebo vpravo). Zachycení myši je uvolněna před tuto událost je aktivována.<br /><br /> Záznam mapy událostí: **EVENT_STOCK_MOUSEUP( )**|
|ReadyStateChange|**void FireReadyStateChange( )**|Aktivováno při přechodu ovládacího prvku do dalšího stavu připravenosti z důvodu množství přijatých dat.<br /><br /> Záznam mapy událostí: **EVENT_STOCK_READYSTATECHANGE( )**|

## <a name="adding-a-stock-event-using-the-add-event-wizard"></a><a name="_core_adding_a_stock_event_using_classwizard"></a>Přidání burzovní události pomocí Průvodce přidáním události

Přidání burzovních událostí vyžaduje méně práce než přidání vlastních událostí, `COleControl`protože vypalování skutečné události je automaticky zpracováno základní třídou . Následující postup přidá akciovou událost do ovládacího prvku, který byl vyvinut pomocí [Průvodce řízením ActiveX knihovny MFC](../mfc/reference/mfc-activex-control-wizard.md). Událost, nazývaná KeyPress, se aktivuje, když je stisknuta klávesa a ovládací prvek je aktivní. Tento postup lze také přidat další události zásob. Nahraďte vybraný název akciové události klávesou KeyPress.

#### <a name="to-add-the-keypress-stock-event-using-the-add-event-wizard"></a>Přidání akciové události KeyPress pomocí Průvodce přidáním události

1. Načtěte projekt ovládacího prvku.

1. V zobrazení třídy otevřete místní nabídku kliknutím pravým tlačítkem myši na třídu ovládacího prvku ActiveX.

1. V místní nabídce klikněte na **Přidat** a potom na **Přidat událost**.

   Otevře se Průvodce přidáním události.

1. V rozevíracím seznamu **Název** `KeyPress`události vyberte položku .

1. Klikněte na **Finish** (Dokončit).

## <a name="add-event-wizard-changes-for-stock-events"></a><a name="_core_classwizard_changes_for_stock_events"></a>Přidat změny Průvodce událostmi pro události na skladě

Vzhledem k tomu, že události zásob jsou zpracovány základní třídou ovládacího prvku, Průvodce přidáním události žádným způsobem nezmění deklaraci třídy. Přidá událost do mapy událostí ovládacího prvku a provede položku v jeho . IDL. Následující řádek je přidán do mapy událostí ovládacího prvku, který se nachází v implementaci třídy řízení (. CPP) soubor:

[!code-cpp[NVC_MFC_AxUI#5](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_1.cpp)]

Přidání tohoto kódu vyvolá událost KeyPress, když je přijata WM_CHAR zpráva a ovládací prvek je aktivní. KeyPress událost může být aktivována jindy voláním jeho `FireKeyPress`funkce vypalování (například) z v rámci řídicího kódu.

Průvodce přidáním události přidá následující řádek kódu ovládacího prvku . IDL soubor:

[!code-cpp[NVC_MFC_AxUI#6](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_2.idl)]

Tento řádek přidruží událost KeyPress k jeho standardníi id odeslání a umožňuje kontejneru předvídat keypress události.

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)<br/>
[MFC – ovládací prvky ActiveX: Metody](../mfc/mfc-activex-controls-methods.md)<br/>
[Třída COleControl](../mfc/reference/colecontrol-class.md)

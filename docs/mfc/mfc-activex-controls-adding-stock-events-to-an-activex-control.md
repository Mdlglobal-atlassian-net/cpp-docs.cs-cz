---
title: 'MFC – ovládací prvky ActiveX: Přidání uložených událostí do ovládacího prvku ActiveX | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cf5cb0ccdfe4b8281cf4a56f798da2c4f85c178b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43199818"
---
# <a name="mfc-activex-controls-adding-stock-events-to-an-activex-control"></a>MFC – ovládací prvky ActiveX: Přidání uložených událostí do ovládacího prvku ActiveX
Uložených událostí se liší od vlastních událostí, v tom, že automaticky při vyvolání třídou [COleControl](../mfc/reference/colecontrol-class.md). `COleControl` obsahuje předdefinované členské funkce, které se aktivují událostí vyplývající z běžné akce. Některé běžné akce implementované `COleControl` zahrnují single - a double - clicks ovládacího prvku, události klávesnice a změny ve stavu tlačítka myši. Položky populace, které události jsou vždy předchází event_stock – předpona mapování události.  
  
##  <a name="_core_stock_events_supported_by_classwizard"></a> Stock podporuje události Průvodce přidáním události  
 `COleControl` Třída poskytuje deset uložených událostí, uvedené v následující tabulce. Můžete zadat událostí, které chcete v pomocí ovládacího prvku [Průvodce přidáním události](../ide/add-event-wizard.md).  
  
### <a name="stock-events"></a>Uložených událostí  
  
|Událost|Ohlásí – funkce|Komentáře|  
|-----------|---------------------|--------------|  
|Klikněte na...|**void (fireclick –)**|Aktivována, když ovládací prvek zachytí myš, všechny **BUTTONUP** přijetí zprávy (levý, střední nebo pravou) a na tlačítko se uvolní nad ovládací prvek. MouseDown akcie a události MouseUp dojít před touto událostí.<br /><br /> Zápis do mapy událostí: **(event_stock_click –)**|  
|DblClick|**void (firedblclick –)**|Podobně jako to Click ale aktivována, pokud **BUTTONDBLCLK** doručení zprávy.<br /><br /> Zápis do mapy událostí: **(event_stock_dblclick –)**|  
|Chyba|**fireerror – void (SCODE***scode* **, LPCSTR** `lpszDescription` **, UINT**`nHelpID`**= 0)** |Je aktivována při výskytu chyby v rámci ovládacího prvku ActiveX mimo rozsah přístup metody volání nebo vlastnost.<br /><br /> Zápis do mapy událostí: **(event_stock_errorevent –)**|  
|KeyDown|**firekeydown – void (krátký** `nChar` **krátká**`nShiftState`**)** |Aktivováno, když `WM_SYSKEYDOWN` nebo `WM_KEYDOWN` doručení zprávy.<br /><br /> Zápis do mapy událostí: **(event_stock_keydown –)**|  
|KeyPress|**firekeypress – void (krátký** <strong>\*</strong> `pnChar` **)** |Aktivováno, když `WM_CHAR` doručení zprávy.<br /><br /> Zápis do mapy událostí: **EVENT_STOCK_KEYPRESS)**|  
|KeyUp|**firekeyup – void (krátký** `nChar` **krátká**`nShiftState`**)** |Aktivováno, když `WM_SYSKEYUP` nebo `WM_KEYUP` doručení zprávy.<br /><br /> Zápis do mapy událostí: **(event_stock_keyup –)**|  
|MouseDown|**firemousedown – void (krátký** `nButton` **krátká** `nShiftState` **, float***x* **, float** *y***)** |Odesláno, pokud žádné **STISKNUTITLACITKA** přijetí (doleva, střední nebo doprava). Ukazatel myši je zachycena, bezprostředně před Tato událost se aktivuje.<br /><br /> Zápis do mapy událostí: **(event_stock_mousedown –)**|  
|MouseMove|**firemousemove – void (krátký** `nButton` **krátká** `nShiftState` **, float***x* **, float** *y***)** |Je aktivována při doručení zprávy do wm_mousemove a.<br /><br /> Zápis do mapy událostí: **(event_stock_mousemove –)**|  
|MouseUp|**firemouseup – void (krátký** `nButton` **krátká** `nShiftState` **, float***x* **, float** *y***)** |Odesláno, pokud žádné **BUTTONUP** přijetí (doleva, střední nebo doprava). Zachycení myši je uvolněn předtím, než se tato událost se aktivuje.<br /><br /> Zápis do mapy událostí: **(event_stock_mouseup –)**|  
|ReadyStateChange|**void (FireReadyStateChange)**|Je aktivována při řízení přejde na další připravena kvůli množství dat přijatých.<br /><br /> Zápis do mapy událostí: **(event_stock_readystatechange –)**|  
  
##  <a name="_core_adding_a_stock_event_using_classwizard"></a> Přidání uložených událostí pomocí Průvodce přidáním události  
 Přidání uložených událostí vyžaduje méně práce než přidání vlastních událostí, protože jeho spuštění skutečné události je automaticky zpracována třídou base `COleControl`. Následující procedura přidá uložených událostí do ovládacího prvku, která byla vyvinutá pomocí [Průvodce ovládacím prvkem MFC ActiveX](../mfc/reference/mfc-activex-control-wizard.md). Události, volá KeyPress, aktivuje se v případě stisknutí klávesy a ovládací prvek není aktivní. Tento postup lze také přidat další uložených událostí. Nahraďte název vybrané základní událost KeyPress.  
  
#### <a name="to-add-the-keypress-stock-event-using-the-add-event-wizard"></a>Chcete-li přidat základní událost KeyPress pomocí Průvodce přidáním události  
  
1.  Načtení projektu ovládacího prvku.  
  
2.  V zobrazení tříd klikněte pravým tlačítkem na třídy vašeho ovládacího prvku ActiveX otevřete místní nabídku.  
  
3.  V místní nabídce klikněte na tlačítko **přidat** a potom klikněte na tlačítko **přidat událost**.  
  
     Otevře se Průvodce přidáním události.  
  
4.  V **název události** rozevíracího seznamu vyberte `KeyPress`.  
  
5.  Klikněte na tlačítko **Dokončit**.  
  
##  <a name="_core_classwizard_changes_for_stock_events"></a> Přidejte změny událostí, které průvodce pro uložených událostí  
 Protože uložených událostí jsou zpracovány základní třídy ovládacího prvku, Průvodce přidáním události deklaraci vaší třídy nijak nezmění. Přidá událost do mapy ovládacího prvku událost a vytvoří záznam v jeho. Soubor IDL. Následující řádek je přidán do mapování události ovládacího prvku, v implementaci třídy ovládacího prvku (. Soubor CPP):  
  
 [!code-cpp[NVC_MFC_AxUI#5](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_1.cpp)]  
  
 Přidání tohoto kódu aktivuje události KeyPress. když se zpráva WM_CHAR a ovládací prvek je aktivní. Je tato událost může být aktivována v jinou dobu voláním funkce jeho spuštění (například `FireKeyPress`) z kódu ovládacího prvku.  
  
 Průvodce přidáním události přidá následující řádek kódu do ovládacího prvku. Soubor IDL:  
  
 [!code-cpp[NVC_MFC_AxUI#6](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_2.idl)]  
  
 Tento řádek přidruží události KeyPress standard dispatch ID a umožňuje kontejneru předvídat události KeyPress.  
  
## <a name="see-also"></a>Viz také  
 [MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)   
 [MFC – ovládací prvky ActiveX: metody](../mfc/mfc-activex-controls-methods.md)   
 [COleControl – třída](../mfc/reference/colecontrol-class.md)

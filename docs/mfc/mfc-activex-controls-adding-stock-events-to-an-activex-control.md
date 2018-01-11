---
title: "Ovládací prvky MFC ActiveX: Přidání uložených událostí do ovládacího prvku ActiveX | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
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
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 99de785bba9f566c5dbb4751f788320b96782427
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-adding-stock-events-to-an-activex-control"></a>MFC – ovládací prvky ActiveX: Přidání uložených událostí do ovládacího prvku ActiveX
Uložených událostí se liší od vlastních událostí v tom, že jsou automaticky aktivována třída [COleControl](../mfc/reference/colecontrol-class.md). `COleControl`obsahuje předdefinované členské funkce, které budou spuštěny událostí vyplývající z běžné akce. Některé běžné akce implementované `COleControl` zahrnují single - a double - clicks na ovládací prvek, události klávesnice a změny ve stavu tlačítka myši. Záznamy událostí mapy pro uložených událostí jsou vždy uvedeny **event_stock –** předponu.  
  
##  <a name="_core_stock_events_supported_by_classwizard"></a>Stock události nepodporuje Průvodce přidáním události  
 `COleControl` Třída poskytuje deset uložených událostí uvedené v následující tabulce. Můžete zadat událostí, které chcete v pomocí ovládacího prvku [Průvodce přidáním události](../ide/add-event-wizard.md).  
  
### <a name="stock-events"></a>Uložených událostí  
  
|Událost|Aktivuje – funkce|Komentáře|  
|-----------|---------------------|--------------|  
|Klikněte na...|**void (fireclick –)**|Aktivována, jestliže ovládacího prvku zaznamená myši, všechny **BUTTONUP** doručení zprávy (vlevo, střední nebo vpravo) a na tlačítko vydání prostřednictvím ovládacího prvku. Stock MouseDown a MouseUp události předcházet této události.<br /><br /> Položku mapování události: **(event_stock_click –)**|  
|DblClick|**void (firedblclick –)**|Podobá se klikněte na tlačítko ale aktivována, pokud **BUTTONDBLCLK** je přijatá zpráva.<br /><br /> Položku mapování události: **(event_stock_dblclick –)**|  
|Chyba|**fireerror – void (kód SCODE***kód scode* **, LPCSTR** `lpszDescription` **, UINT**`nHelpID`**= 0)** |Aktivována, jestliže dojde k chybě v rámci vaší ovládací prvek ActiveX mimo obor metoda volání nebo vlastnost přístup.<br /><br /> Položku mapování události: **(event_stock_errorevent –)**|  
|KeyDown –|**firekeydown – void (krátký** `nChar` **, krátké**`nShiftState`**)** |Aktivováno při `WM_SYSKEYDOWN` nebo `WM_KEYDOWN` je přijatá zpráva.<br /><br /> Položku mapování události: **(event_stock_keydown –)**|  
|KeyPress –|**firekeypress – void (krátký\***`pnChar`**)** |Aktivováno při `WM_CHAR` je přijatá zpráva.<br /><br /> Položku mapování události: **(event_stock_keypress –)**|  
|KeyUp|**firekeyup – void (krátký** `nChar` **, krátké**`nShiftState`**)** |Aktivováno při `WM_SYSKEYUP` nebo `WM_KEYUP` je přijatá zpráva.<br /><br /> Položku mapování události: **(event_stock_keyup –)**|  
|MouseDown –|**firemousedown – void (krátký** `nButton` **, krátké** `nShiftState` **, float***x* **, float** *y***)** |Aktivováno případných **BUTTONDOWN** přijetí (doleva, střední nebo doprava). Myš zachycenou bezprostředně před Tato událost je aktivována.<br /><br /> Položku mapování události: **(event_stock_mousedown –)**|  
|MouseMove –|**firemousemove – void (krátký** `nButton` **, krátké** `nShiftState` **, float***x* **, float** *y***)** |Aktivováno při `WM_MOUSEMOVE` je přijatá zpráva.<br /><br /> Položku mapování události: **(event_stock_mousemove –)**|  
|MouseUp|**firemouseup – void (krátký** `nButton` **, krátké** `nShiftState` **, float***x* **, float** *y***)** |Aktivováno případných **BUTTONUP** přijetí (doleva, střední nebo doprava). Zachycení myši vydání předtím, než tato událost je aktivována.<br /><br /> Položku mapování události: **(event_stock_mouseup –)**|  
|ReadyStateChange –|**void (FireReadyStateChange)**|Aktivována, jestliže řízení přechody do dalšího připravené stavu z důvodu přijatá data.<br /><br /> Položku mapování události: **(event_stock_readystatechange –)**|  
  
##  <a name="_core_adding_a_stock_event_using_classwizard"></a>Přidání uložených událostí pomocí Průvodce přidáním události  
 Přidání uložených událostí vyžaduje méně práce než přidání vlastních událostí, protože pálení skutečné události se automaticky zpracovává základní třídou `COleControl`. Následující postup přidá uložených událostí do ovládacího prvku, která byla vyvinuta pomocí [Průvodce ovládacím prvkem ActiveX knihovny MFC](../mfc/reference/mfc-activex-control-wizard.md). Události, názvem KeyPress, aktivuje se při stisknutí klávesy a řízení je aktivní. Tento postup lze také přidat další uložených událostí. Nahraďte název vybrané uložené události KeyPress.  
  
#### <a name="to-add-the-keypress-stock-event-using-the-add-event-wizard"></a>Chcete-li přidat KeyPress – událost uložené pomocí Průvodce přidáním události  
  
1.  Načtení projektu ovládacího prvku.  
  
2.  V zobrazení tříd klikněte pravým tlačítkem na třídě ovládacího prvku ActiveX a místní nabídce.  
  
3.  V místní nabídce klikněte na **přidat** a pak klikněte na **přidání události**.  
  
     Otevře se Průvodce přidáním události.  
  
4.  V **název události** rozevíracího seznamu vyberte `KeyPress`.  
  
5.  Klikněte na tlačítko **Dokončit**.  
  
##  <a name="_core_classwizard_changes_for_stock_events"></a>Přidání události průvodce změní pro uložených událostí  
 Protože uložených událostí zpracovává základní třídy ovládacího prvku, Průvodce přidání události deklarace třídy nijak nezmění. Přidá událost mapa událostí ovládacího prvku a vytvoří položku v jeho. IDL soubor. Následující řádek je přidán do ovládacího prvku mapa událostí, umístěný v implementaci třídy ovládacího prvku (. Soubor CPP):  
  
 [!code-cpp[NVC_MFC_AxUI#5](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_1.cpp)]  
  
 Přidání tohoto kódu aktivuje KeyPress – událost při `WM_CHAR` přijata zpráva a řízení je aktivní. KeyPress – událost může být aktivována v jinou dobu voláním její funkce pálení (například `FireKeyPress`) z kódu ovládacího prvku.  
  
 Průvodce přidáním události přidá do ovládacího prvku následující řádek kódu. IDL soubor:  
  
 [!code-cpp[NVC_MFC_AxUI#6](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_2.idl)]  
  
 Tento řádek přidruží KeyPress – událost s ID jeho standardní odesílání a umožňuje kontejneru předvídat KeyPress – událost.  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky MFC ActiveX](../mfc/mfc-activex-controls.md)   
 [MFC – ovládací prvky ActiveX: metody](../mfc/mfc-activex-controls-methods.md)   
 [COleControl – třída](../mfc/reference/colecontrol-class.md)

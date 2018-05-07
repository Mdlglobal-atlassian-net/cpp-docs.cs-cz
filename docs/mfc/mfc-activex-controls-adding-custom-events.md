---
title: 'Ovládací prvky MFC ActiveX: Přidání vlastních událostí | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], events [MFC]
- EVENT_CUSTOM prefix [MFC]
- custom events [MFC], adding to ActiveX controls
- EVENT_CUSTOM macro [MFC]
- InCircle method [MFC]
- ClickIn event
- FireClickIn event
- COleControl class [MFC], custom events [MFC]
- Click event, custom events [MFC]
- events [MFC], ActiveX controls
- custom events [MFC]
- FireEvent method, adding custom events
ms.assetid: c584d053-1e34-47aa-958e-37d3e9b85892
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5b82232b8f2ad7a5e3bc1ff8fed0e8a38b1a7d66
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-activex-controls-adding-custom-events"></a>MFC – ovládací prvky ActiveX: Přidání vlastních událostí
Vlastní události lišit od uložených událostí v tom, že nejsou automaticky aktivována třídou `COleControl`. Vlastní události rozpozná určité akce, dáno vývojář ovládacího prvku, jako událost. Položky mapy událostí pro vlastní události jsou reprezentované pomocí `EVENT_CUSTOM` makro. V následující části implementuje vlastní události pro projekt ovládací prvek ActiveX, který byl vytvořen pomocí Průvodce ovládacím prvkem ActiveX.  
  
##  <a name="_core_adding_a_custom_event_with_classwizard"></a> Přidání vlastních událostí pomocí Průvodce přidáním události  
 Následující postup přidá konkrétní vlastní události, clickin –. Tento postup slouží k přidání dalších vlastních událostí. Nahraďte název vlastní události a jeho parametry pro název události clickin – a parametry.  
  
#### <a name="to-add-the-clickin-custom-event-using-the-add-event-wizard"></a>Chcete-li přidat vlastní události clickin – pomocí Průvodce přidáním události  
  
1.  Načtení projektu ovládacího prvku.  
  
2.  V zobrazení tříd klikněte pravým tlačítkem na třídě ovládacího prvku ActiveX a místní nabídce.  
  
3.  V místní nabídce klikněte na **přidat** a pak klikněte na **přidání události**.  
  
     Otevře se Průvodce přidáním události.  
  
4.  V **název události** pole, nejprve vyberte všechny existující událost a pak klikněte na **vlastní** přepínač tlačítko, a pak zadejte `ClickIn`.  
  
5.  V **interní název** zadejte název funkce pálení události. V tomto příkladu použijte výchozí hodnotu poskytované Průvodce přidání události (`FireClickIn`).  
  
6.  Přidat parametr s názvem `xCoord` (typ `OLE_XPOS_PIXELS`) pomocí **název parametru** a **typ parametru** ovládací prvky.  
  
7.  Přidat druhý parametr, s názvem `yCoord` (typ `OLE_YPOS_PIXELS`).  
  
8.  Klikněte na tlačítko **Dokončit** k vytvoření události.  
  
##  <a name="_core_classwizard_changes_for_custom_events"></a> Přidání události průvodce změní pro vlastní události  
 Když přidáte vlastní události, provede Průvodce přidání události změny třída ovládacích prvků. H. CPP, a. Soubory IDL. Následující ukázky kódu jsou specifické pro clickin – událost.  
  
 Následující řádky jsou přidány do záhlaví (. H) soubor třídy ovládacího prvku:  
  
 [!code-cpp[NVC_MFC_AxUI#7](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_1.h)]  
  
 Tento kód deklaruje vložená funkce volá `FireClickIn` , který volá [COleControl::FireEvent](../mfc/reference/colecontrol-class.md#fireevent) s parametry data a clickin – událost můžete definovat pomocí Průvodce přidáním události.  
  
 Kromě toho následující řádek je přidán do mapa událostí pro ovládací prvek nachází v implementaci (. Soubor CPP) třídy ovládacího prvku:  
  
 [!code-cpp[NVC_MFC_AxUI#8](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_2.cpp)]  
  
 Tento kód mapuje clickin – událost vložená funkce `FireClickIn`, předávání parametry definované pomocí Průvodce přidáním události.  
  
 Nakonec se přidá následující řádek do ovládacího prvku. IDL soubor:  
  
 [!code-cpp[NVC_MFC_AxUI#9](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_3.idl)]  
  
 Tento řádek přiřadí clickin – událost na konkrétní číslo ID prováděné z pozice události v seznamu událostí Průvodce přidáním události. Položky v seznamu těchto událostí umožňuje kontejner odhadnout události. Například je může poskytnout kód obslužné rutiny, které budou spuštěny při událost je aktivována.  
  
##  <a name="_core_calling_fireclickin"></a> Fireclickin – volání  
 Teď, když jste přidali vlastní události clickin – pomocí Průvodce přidáním události, musíte rozhodnout, když se tato událost má být aktivována. To provedete pomocí volání `FireClickIn` případech příslušnou akci. V tomto výkladu používá ovládacího prvku `InCircle` funkce uvnitř `WM_LBUTTONDOWN` popisovač zpráv se má provést clickin – událost, když uživatel klikne v kruhových nebo eliptické oblast. Následující postup přidá `WM_LBUTTONDOWN` obslužné rutiny.  
  
#### <a name="to-add-a-message-handler-with-the-add-event-wizard"></a>Přidání obslužné rutiny zpráv pomocí Průvodce přidáním události  
  
1.  Načtení projektu ovládacího prvku.  
  
2.  V zobrazení tříd vyberte třídě ovládacího prvku ActiveX.  
  
3.  V okně vlastností klikněte **zprávy** tlačítko.  
  
     V okně Vlastnosti se zobrazí seznam zpráv, které mohou být zpracovány ovládací prvek ActiveX. Jakékoli zprávy zobrazeny tučně již má přiřazen funkci obslužné rutiny.  
  
4.  V okně Vlastnosti vyberte zprávu, kterou chcete zpracovat. V tomto příkladu vyberte `WM_LBUTTONDOWN`.  
  
5.  Z rozevíracího seznamu na pravé straně, vyberte  **\<Přidat > onlbuttondown –**.  
  
6.  Dvakrát klikněte na nové funkce v zobrazení tříd pro přechod na kód obslužné rutiny zpráv k implementaci obslužné rutiny (. Soubor CPP) ovládacího prvku ActiveX.  
  
 Následující kód Ukázka volání **incircle –** funkce pokaždé, když v okně řízení kliknutí na něj. Tato ukázka najdete v `WM_LBUTTONDOWN` obslužné rutiny funkce `OnLButtonDown`v [str ukázka](../visual-cpp-samples.md) abstraktní.  
  
 [!code-cpp[NVC_MFC_AxUI#10](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_4.cpp)]  
  
> [!NOTE]
>  Když Průvodce přidání události vytváří obslužné rutiny zpráv pro tlačítko akce myši, se automaticky přidá volání popisovač zpráv základní třídy. Neodebírejte toto volání. Pokud vlastní ovládací prvek využívá všechny zprávy uložených myš, musí být voláno obslužné rutiny zpráv v základní třídě zajistit, že je správně zajistit zachycení myši.  
  
 V následujícím příkladu aktivuje událost při kliknutím na možnost dochází pouze uvnitř kruhových nebo eliptické oblasti v ovládacím prvku. K dosažení toto chování, můžete umístit `InCircle` funkce v implementaci ovládacího prvku (. Soubor CPP):  
  
 [!code-cpp[NVC_MFC_AxUI#11](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_5.cpp)]  
  
 Budete také muset přidat následující deklaraci `InCircle` funkce ovládacího prvku záhlaví (. H) soubor:  
  
 [!code-cpp[NVC_MFC_AxUI#12](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_6.h)]  
  
##  <a name="_core_custom_events_with_stock_names"></a> Vlastní události s názvy uložených  
 Můžete vytvořit vlastní události se stejným názvem jako uložených událostí, ale nelze implementovat v stejný ovládací prvek. Můžete například vytvořit vlastní události názvem kliknutím, který neaktivuje při uložených událostí klikněte na tlačítko by za normálních okolností aktivovat. Klikněte na událost může pak vyvolání kdykoli voláním jeho pálení funkce.  
  
 Následující postup přidá vlastní klikněte na události.  
  
#### <a name="to-add-a-custom-event-that-uses-a-stock-event-name"></a>Chcete-li přidat vlastní události, které používá název uložených událostí  
  
1.  Načtení projektu ovládacího prvku.  
  
2.  V zobrazení tříd klikněte pravým tlačítkem na třídě ovládacího prvku ActiveX a místní nabídce.  
  
3.  V místní nabídce klikněte na **přidat** a pak klikněte na **přidání události**.  
  
     Otevře se Průvodce přidáním události.  
  
4.  V **název události** rozevíracího seznamu vyberte název uložené události. V tomto příkladu vyberte **klikněte na tlačítko**.  
  
5.  Pro **typ události**, vyberte **vlastní**.  
  
6.  Klikněte na tlačítko **Dokončit** k vytvoření události.  
  
7.  Volání `FireClick` na příslušná místa v kódu.  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky MFC ActiveX](../mfc/mfc-activex-controls.md)   
 [MFC – ovládací prvky ActiveX: metody](../mfc/mfc-activex-controls-methods.md)   
 [COleControl – třída](../mfc/reference/colecontrol-class.md)

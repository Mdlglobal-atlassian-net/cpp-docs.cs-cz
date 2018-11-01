---
title: 'MFC – ovládací prvky ActiveX: Přidání vlastních událostí'
ms.date: 11/04/2016
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
ms.openlocfilehash: ad44cb097f03270b09612ad756d34725464a1765
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50554905"
---
# <a name="mfc-activex-controls-adding-custom-events"></a>MFC – ovládací prvky ActiveX: Přidání vlastních událostí

Vlastní události liší od uložených událostí, že se automaticky aktivuje třídou `COleControl`. Vlastní události rozpoznává určité akce, určí vývojářem ovládacích prvků, jako událost. Události položek mapování pro vlastní události jsou reprezentovány EVENT_CUSTOM – makro. Následující části implementuje vlastní události pro projekt ovládacího prvku ActiveX, který byl vytvořen pomocí Průvodce ovládacím prvkem ActiveX.

##  <a name="_core_adding_a_custom_event_with_classwizard"></a> Přidání vlastních událostí s Průvodce přidáním události

Následující procedura přidá určité vlastní události, clickin –. Tento postup slouží k přidání dalších vlastních událostí. Nahraďte název vaší vlastní události a jeho parametry pro název clickin – událost a parametry.

#### <a name="to-add-the-clickin-custom-event-using-the-add-event-wizard"></a>Chcete-li přidat vlastní událost clickin – pomocí Průvodce přidáním události

1. Načtení projektu ovládacího prvku.

1. V zobrazení tříd klikněte pravým tlačítkem na třídy vašeho ovládacího prvku ActiveX otevřete místní nabídku.

1. V místní nabídce klikněte na tlačítko **přidat** a potom klikněte na tlačítko **přidat událost**.

   Otevře se Průvodce přidáním události.

1. V **název události** pole, nejprve vyberte jakékoli existující události a poté klikněte na **vlastní** přepínač tlačítko a pak zadejte *clickin –*.

1. V **interní název** zadejte název funkce události jeho spuštění. V tomto příkladu použijte výchozí hodnotu poskytované Průvodce přidání události (`FireClickIn`).

1. Přidat parametr s názvem *xCoord* (typ *OLE_XPOS_PIXELS*), použije **název parametru** a **typ parametru** ovládacích prvků.

1. Přidejte druhý parametr, s názvem *yCoord* (typ *OLE_YPOS_PIXELS*).

1. Klikněte na tlačítko **Dokončit** vytvořit událost.

##  <a name="_core_classwizard_changes_for_custom_events"></a> Přidejte změny událostí, které průvodce pro vlastní události

Když přidáte vlastní událost, provede Průvodce přidáním události změny třídy ovládacího prvku. H. CPP, a. Soubory IDL. Následující ukázky kódu jsou specifické pro clickin – událost.

Následující řádky se přidají do záhlaví (. H) soubor třídy vašeho ovládacího prvku:

[!code-cpp[NVC_MFC_AxUI#7](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_1.h)]

Tento kód deklaruje vložená funkce volána `FireClickIn` , která volá [COleControl::FireEvent](../mfc/reference/colecontrol-class.md#fireevent) s parametry a clickin – událost můžete definovat pomocí Průvodce přidáním události.

Kromě toho se přidá následující řádek do mapy událostí pro ovládací prvek umístěný v implementaci (. Soubor CPP) třídy ovládacího prvku:

[!code-cpp[NVC_MFC_AxUI#8](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_2.cpp)]

Tento kód se mapuje na vložené funkce clickin – událost `FireClickIn`, předávání parametrů můžete definovat pomocí Průvodce přidáním události.

Nakonec se přidá následující řádek do ovládacího prvku. Soubor IDL:

[!code-cpp[NVC_MFC_AxUI#9](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_3.idl)]

Tento řádek přiřadí clickin – událost konkrétní identifikační číslo, na základě pozice události v seznamu událostí Průvodce přidáním události. Položka v seznamu událostí umožňuje kontejner předvídat události. Je třeba zadat kód obslužné rutiny, který se spustí, když se aktivuje událost.

##  <a name="_core_calling_fireclickin"></a> Fireclickin – volání

Teď, když jste přidali vlastní událost clickin – pomocí Průvodce přidáním události, musíte rozhodnout, kdy je tato událost se aktivuje. To lze provést zavoláním `FireClickIn` při výskytu příslušnou akci. V tomto výkladu používá ovládací prvek `InCircle` funkci uvnitř obslužné rutiny zpráv WM_LBUTTONDOWN Chcete-li vyvolat clickin – událost, když uživatel klikne do kruhové nebo elipsy oblasti. Následující procedura přidá obslužnou rutinu WM_LBUTTONDOWN.

#### <a name="to-add-a-message-handler-with-the-add-event-wizard"></a>Chcete-li přidat obslužné rutiny zpráv pomocí Průvodce přidáním události

1. Načtení projektu ovládacího prvku.

1. V zobrazení tříd vyberte třídy vašeho ovládacího prvku ActiveX.

1. V okně Vlastnosti klikněte na tlačítko **zprávy** tlačítko.

   V okně Vlastnosti se zobrazí seznam zpráv, které mohou být zpracovány ovládací prvek ActiveX. Všechny zprávy zobrazeny tučně již má funkci obslužné rutiny přiřazenou.

1. V okně Vlastnosti vyberte zprávu, kterou chcete zpracovat. V tomto příkladu vyberte WM_LBUTTONDOWN.

1. Z rozevíracího seznamu na pravé straně vyberte  **\<Přidat > onlbuttondown –**.

1. Dvakrát klikněte na novou funkci obslužné rutiny v zobrazení tříd pro přechod na kód obslužné rutiny zprávy v implementaci (. Soubor CPP) ovládacího prvku ActiveX.

Následující kód volá ukázka `InCircle` pracovat pokaždé, když dojde ke kliknutí na levé tlačítko myši v rámci okna ovládacího prvku. Tato ukázka najdete ve funkci obslužné rutiny WM_LBUTTONDOWN `OnLButtonDown`v [KR ukázka](../visual-cpp-samples.md) abstraktní.

[!code-cpp[NVC_MFC_AxUI#10](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_4.cpp)]

> [!NOTE]
>  Když Průvodce přidáním události vytvoří obslužné rutiny zpráv pro akce tlačítka myši, se automaticky přidá volání stejné obslužná rutina zprávy základní třídy. Neodebírejte toto volání. Pokud váš ovládací prvek používá některou z zprávy uložených týkající se myši, obslužné rutiny zpráv v základní třídě musí být volána k zajištění, že se správně zpracovává zachycení myši.

V následujícím příkladu se událost aktivuje při kliknutím na dochází pouze uvnitř zacyklená nebo elipsy oblasti v ovládacím prvku. K dosažení tohoto chování, můžete umístit `InCircle` funkce v implementaci ovládacího prvku (. Soubor CPP):

[!code-cpp[NVC_MFC_AxUI#11](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_5.cpp)]

Budete také muset přidat následující typ deklarace `InCircle` funkce do ovládacího prvku záhlaví (. H) file:

[!code-cpp[NVC_MFC_AxUI#12](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_6.h)]

##  <a name="_core_custom_events_with_stock_names"></a> Vlastní události s názvy uložených

Se stejným názvem jako uložených událostí, můžete vytvořit vlastní události, ale nemůže implementovat v stejný ovládací prvek. Můžete například chtít vytvořit vlastní události, volá se, která se neaktivuje, když základní událost kliknutí by normálně aktivují, klikněte na tlačítko. Může pak vyvolat událost Click kdykoli po zavolání funkce jeho spuštění.

Následující procedura přidá vlastní klikněte na událost.

#### <a name="to-add-a-custom-event-that-uses-a-stock-event-name"></a>Chcete-li přidat vlastní událost, která používá název základní událost

1. Načtení projektu ovládacího prvku.

1. V zobrazení tříd klikněte pravým tlačítkem na třídy vašeho ovládacího prvku ActiveX otevřete místní nabídku.

1. V místní nabídce klikněte na tlačítko **přidat** a potom klikněte na tlačítko **přidat událost**.

   Otevře se Průvodce přidáním události.

1. V **název události** rozevíracího seznamu vyberte název základní událost. V tomto příkladu vyberte **klikněte na tlačítko**.

1. Pro **typ události**vyberte **vlastní**.

1. Klikněte na tlačítko **Dokončit** vytvořit událost.

1. Volání `FireClick` na příslušných místech ve vašem kódu.

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)<br/>
[MFC – ovládací prvky ActiveX: Metody](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl – třída](../mfc/reference/colecontrol-class.md)

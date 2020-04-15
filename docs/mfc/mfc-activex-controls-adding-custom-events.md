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
ms.openlocfilehash: 8d464e5d7c9731e158e44d66d569fd1555401e17
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364721"
---
# <a name="mfc-activex-controls-adding-custom-events"></a>MFC – ovládací prvky ActiveX: Přidání vlastních událostí

Vlastní události se liší od události zásob v `COleControl`tom, že nejsou automaticky aktivována třídy . Vlastní událost rozpozná určitou akci určenou vývojářem ovládacího prvku jako událost. Položky mapy událostí pro vlastní události jsou reprezentovány EVENT_CUSTOM makro. Následující část implementuje vlastní událost pro projekt ovládacího prvku ActiveX, který byl vytvořen pomocí Průvodce ovládacím prvkem ActiveX.

## <a name="adding-a-custom-event-with-the-add-event-wizard"></a><a name="_core_adding_a_custom_event_with_classwizard"></a>Přidání vlastní události pomocí Průvodce přidáním události

Následující postup přidá konkrétní vlastní událost ClickIn. Tento postup můžete použít k přidání dalších vlastních událostí. Nahraďte název události vlastní události a její parametry názvem a parametry události ClickIn.

#### <a name="to-add-the-clickin-custom-event-using-the-add-event-wizard"></a>Přidání vlastní události ClickIn pomocí Průvodce přidáním události

1. Načtěte projekt ovládacího prvku.

1. V **zobrazení třídy**klepnutím pravým tlačítkem myši na třídu ovládacího prvku ActiveX otevřete místní nabídku.

1. V místní nabídce klikněte na **Přidat** a potom na **Přidat událost**.

   Otevře se Průvodce přidáním události.

1. V poli **Název události** nejprve vyberte existující událost, poté klikněte na **tlačítko Vlastní** přepínací a zadejte *příkaz ClickIn*.

1. Do pole **Vnitřní název** zadejte název funkce spouštění události. V tomto příkladu použijte výchozí hodnotu poskytovanou Průvodcem přidáním události (`FireClickIn`).

1. Přidejte parametr s názvem *xCoord* (typ *OLE_XPOS_PIXELS*) pomocí ovládacích prvků **Název parametru** a **Typ parametru.**

1. Přidejte druhý parametr, nazývaný *yCoord* (typ *OLE_YPOS_PIXELS*).

1. Kliknutím na **Dokončit** vytvořte událost.

## <a name="add-event-wizard-changes-for-custom-events"></a><a name="_core_classwizard_changes_for_custom_events"></a>Přidat změny Průvodce událostmi pro vlastní události

Když přidáte vlastní událost, Průvodce přidáním události provede změny ve třídě ovládacího prvku . H. CPP a . IDL soubory. Následující ukázky kódu jsou specifické pro událost ClickIn.

Do záhlaví jsou přidány následující řádky (. H) soubor vaší třídy řízení:

[!code-cpp[NVC_MFC_AxUI#7](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_1.h)]

Tento kód deklaruje `FireClickIn` váděnou funkci volanou [voláním COleControl::FireEvent](../mfc/reference/colecontrol-class.md#fireevent) s událostí ClickIn a parametry, které jste definovali pomocí Průvodce přidáním události.

Kromě toho je následující řádek přidán do mapy událostí pro ovládací prvek, který se nachází v implementaci (. CPP) vaší třídy řízení:

[!code-cpp[NVC_MFC_AxUI#8](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_2.cpp)]

Tento kód mapuje událost ClickIn `FireClickIn`na válčící funkci a předá parametry, které jste definovali pomocí Průvodce přidáním události.

Nakonec je do ovládacího prvku přidán následující řádek . IDL soubor:

[!code-cpp[NVC_MFC_AxUI#9](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_3.idl)]

Tento řádek přiřadí události ClickIn určité id číslo převzaté z pozice události v seznamu událostí Přidat Průvodce událostí. Položka v seznamu událostí umožňuje kontejneru předvídat událost. Například může poskytnout kód obslužné rutiny, který má být proveden při spuštění události.

## <a name="calling-fireclickin"></a><a name="_core_calling_fireclickin"></a>Volání FireClickIn

Nyní, když jste přidali ClickIn vlastní událost pomocí Průvodce přidáním události, musíte rozhodnout, kdy má být tato událost aktivována. To provést voláním, `FireClickIn` když dojde k příslušné akci. Pro tuto diskusi ovládací `InCircle` prvek používá `WM_LBUTTONDOWN` funkci uvnitř obslužné rutiny zprávy k požáru clickin událost, když uživatel klepne uvnitř kruhové nebo eliptické oblasti. Následující postup přidá `WM_LBUTTONDOWN` obslužnou rutinu.

#### <a name="to-add-a-message-handler-with-the-add-event-wizard"></a>Přidání obslužné rutiny zprávy pomocí Průvodce přidáním události

1. Načtěte projekt ovládacího prvku.

1. V **zobrazení tříd**vyberte třídu ovládacího prvku ActiveX.

1. V okně **Vlastnosti** se zobrazí seznam zpráv, které mohou být zpracovány ovládacím prvkem ActiveX. Všechny zprávy zobrazené tučně již mají přiřazenu funkci obslužné rutiny.

1. Vyberte zprávu, kterou chcete zpracovat. V tomto příkladu vyberte . `WM_LBUTTONDOWN`

1. V rozevíracím seznamu vpravo vyberte ** \<Přidat> OnLButtonDown**.

1. Poklepáním na novou funkci obslužné rutiny v **zobrazení třídy** přejděte na kód obslužné rutiny zprávy v implementaci (. CPP) ovládacího prvku ActiveX.

Následující ukázka kódu `InCircle` volá funkci pokaždé, když klepnete na levé tlačítko myši v okně ovládacího prvku. Tento vzorek lze nalézt `WM_LBUTTONDOWN` ve `OnLButtonDown`funkci obslužné rutiny , v [circ ukázkový](../overview/visual-cpp-samples.md) abstrakt.

[!code-cpp[NVC_MFC_AxUI#10](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_4.cpp)]

> [!NOTE]
> Když Průvodce přidáním události vytvoří obslužné rutiny zpráv pro akce tlačítka myši, automaticky se přidá volání stejné obslužné rutiny zprávy základní třídy. Neodstraňujte tento hovor. Pokud ovládací prvek používá některou ze zpráv myši populace, obslužné rutiny zpráv v základní třídě musí být volána k zajištění, že zachycení myši je správně zpracována.

V následujícím příkladu událost aktivuje pouze v případě, že dojde k kliknutí uvnitř kruhové nebo eliptické oblasti v rámci ovládacího prvku. Chcete-li dosáhnout tohoto chování, můžete umístit `InCircle` funkci v implementaci ovládacího prvku (. CPP) soubor:

[!code-cpp[NVC_MFC_AxUI#11](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_5.cpp)]

Budete také muset přidat následující deklarace `InCircle` funkce do záhlaví ovládacího prvku (. H) soubor:

[!code-cpp[NVC_MFC_AxUI#12](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_6.h)]

## <a name="custom-events-with-stock-names"></a><a name="_core_custom_events_with_stock_names"></a>Vlastní události s názvy akcií

Můžete vytvořit vlastní události se stejným názvem jako události zásob, ale nemůžete implementovat oba ve stejném ovládacím prvku. Můžete například vytvořit vlastní událost s názvem Click, která se nespálí, když by se normálně ohlašuje akciová událost Click. Pak můžete vypálit událost Click kdykolivoláním její funkce střelby.

Následující postup přidá vlastní Click událost.

#### <a name="to-add-a-custom-event-that-uses-a-stock-event-name"></a>Přidání vlastní události, která používá název akciové události

1. Načtěte projekt ovládacího prvku.

1. V **zobrazení třídy**klepnutím pravým tlačítkem myši na třídu ovládacího prvku ActiveX otevřete místní nabídku.

1. V místní nabídce klikněte na **Přidat** a potom na **Přidat událost**.

   Otevře se Průvodce přidáním události.

1. V rozevíracím seznamu **Název události** vyberte název akciové události. V tomto příkladu vyberte **Klepněte na**tlačítko .

1. V **popřípadě Typ události**vyberte **vlastní**.

1. Kliknutím na **Dokončit** vytvořte událost.

1. Zavolejte `FireClick` na příslušná místa ve vašem kódu.

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)<br/>
[MFC – ovládací prvky ActiveX: Metody](../mfc/mfc-activex-controls-methods.md)<br/>
[Třída COleControl](../mfc/reference/colecontrol-class.md)

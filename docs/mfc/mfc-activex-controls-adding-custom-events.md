---
title: 'MFC – ovládací prvky ActiveX: Přidávání vlastních událostí'
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
ms.openlocfilehash: d22eb6016635c509d6b8bb2068f00125d0227ca2
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907309"
---
# <a name="mfc-activex-controls-adding-custom-events"></a>MFC – ovládací prvky ActiveX: Přidávání vlastních událostí

Vlastní události se liší od uložených událostí v tom, že nejsou automaticky spouštěny `COleControl`třídou. Vlastní událost rozpoznává určitou akci určenou vývojářem ovládacího prvku jako událost. Položky mapování událostí pro vlastní události jsou reprezentovány pomocí makra EVENT_CUSTOM. V následující části je implementována vlastní událost pro projekt ovládacího prvku ActiveX, který byl vytvořen pomocí Průvodce ovládacím prvkem ActiveX.

##  <a name="_core_adding_a_custom_event_with_classwizard"></a>Přidání vlastní události pomocí Průvodce přidáním události

Následující postup přidá konkrétní vlastní událost ClickIn. Pomocí tohoto postupu můžete přidat další vlastní události. Pro název a parametry události ClickIn nahraďte vlastní název události a její parametry.

#### <a name="to-add-the-clickin-custom-event-using-the-add-event-wizard"></a>Přidání vlastní události ClickIn pomocí Průvodce přidáním události

1. Načtěte projekt ovládacího prvku.

1. V **zobrazení tříd**klikněte pravým tlačítkem myši na třídu ovládacího prvku ActiveX a otevřete místní nabídku.

1. V místní nabídce klikněte na **Přidat** a pak klikněte na **Přidat událost**.

   Tím se otevře Průvodce přidáním události.

1. V poli **název události** nejdřív vyberte libovolnou existující událost, potom klikněte na **vlastní** přepínač a zadejte *ClickIn*.

1. Do pole **interní název** zadejte název funkce vyvolávání události. V tomto příkladu použijte výchozí hodnotu poskytnutou průvodcem přidáním události (`FireClickIn`).

1. Přidejte parametr s názvem *xCoord* (typ *OLE_XPOS_PIXELS*) s použitím ovládacích prvků **název parametru** a **typ parametru** .

1. Přidejte druhý parametr nazvaný *yCoord* (typ *OLE_YPOS_PIXELS*).

1. Kliknutím na tlačítko **Dokončit** Vytvořte událost.

##  <a name="_core_classwizard_changes_for_custom_events"></a>Přidat změny Průvodce událostí pro vlastní události

Když přidáte vlastní událost, Průvodce přidáním události provede změny ve třídě ovládacího prvku. H,. CPP a. Soubory IDL Následující ukázky kódu jsou specifické pro událost ClickIn.

Do záhlaví se přidají následující řádky (. H) souboru vaší třídy ovládacího prvku:

[!code-cpp[NVC_MFC_AxUI#7](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_1.h)]

Tento kód deklaruje vloženou funkci nazvanou `FireClickIn` , která volá [COleControl –:: fireEvent](../mfc/reference/colecontrol-class.md#fireevent) s událostí ClickIn a parametry, které jste definovali pomocí Průvodce přidáním události.

Kromě toho se do mapy událostí ovládacího prvku přidá následující řádek, který se nachází v implementaci (. CPP) souboru vaší třídy ovládacího prvku:

[!code-cpp[NVC_MFC_AxUI#8](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_2.cpp)]

Tento kód mapuje Event ClickIn na vloženou funkci `FireClickIn`a předává parametry, které jste definovali pomocí Průvodce přidáním události.

Nakonec se do ovládacího prvku přidá následující řádek. Soubor IDL:

[!code-cpp[NVC_MFC_AxUI#9](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_3.idl)]

Tento řádek přiřadí konkrétní identifikační číslo události ClickIn z pozice události v seznamu událostí Průvodce přidáním události. Položka v seznamu událostí umožňuje kontejneru odhadnout událost. Například může poskytovat kód obslužné rutiny, který se spustí při vyvolání události.

##  <a name="_core_calling_fireclickin"></a>Volání FireClickIn

Teď, když jste přidali vlastní událost ClickIn pomocí Průvodce přidáním události, je nutné se rozhodnout, kdy má být událost aktivována. To provedete tak `FireClickIn` , že zavoláte, když dojde k příslušné akci. Pro tuto diskuzi používá `InCircle` ovládací prvek funkci v `WM_LBUTTONDOWN` rámci obslužné rutiny zpráv k vyvolání události ClickIn, když uživatel klikne dovnitř kruhové nebo elipsovité oblasti. Následující postup přidá `WM_LBUTTONDOWN` obslužnou rutinu.

#### <a name="to-add-a-message-handler-with-the-add-event-wizard"></a>Přidání obslužné rutiny zpráv pomocí Průvodce přidáním události

1. Načtěte projekt ovládacího prvku.

1. V **zobrazení tříd**vyberte svou třídu ovládacího prvku ActiveX.

1. V okně **vlastnosti** se zobrazí seznam zpráv, které mohou být zpracovány ovládacím prvkem ActiveX. Žádná zpráva zobrazená tučně již obsahuje přiřazenou funkci obslužné rutiny.

1. Vyberte zprávu, kterou chcete zpracovat. V tomto příkladu vyberte `WM_LBUTTONDOWN`.

1. V rozevíracím seznamu na pravé straně vyberte  **\<přidat > OnLButtonDown**.

1. Dvojím kliknutím na novou funkci obslužné rutiny v **zobrazení tříd** přejděte na kód obslužné rutiny zprávy v implementaci (. CPP) ovládacího prvku ActiveX.

Následující ukázka kódu volá `InCircle` funkci při každém kliknutí levým tlačítkem myši v okně ovládacího prvku. Tuto ukázku lze nalézt ve `WM_LBUTTONDOWN` `OnLButtonDown`funkci obslužné rutiny, v [ukázce Sample](../overview/visual-cpp-samples.md) abstract.

[!code-cpp[NVC_MFC_AxUI#10](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_4.cpp)]

> [!NOTE]
>  Když Průvodce přidáním události vytvoří obslužné rutiny zpráv pro akce tlačítek myši, bude automaticky přidáno volání stejné obslužné rutiny zprávy základní třídy. Toto volání neodstraňujte. Pokud váš ovládací prvek používá některou z burzovních zpráv myši, musí být zavolány obslužné rutiny zpráv v základní třídě, aby bylo zajištěno, že je zachycení myši správně zpracováno.

V následujícím příkladu se událost aktivuje pouze v případě, že v ovládacím prvku dojde k kliknutí uvnitř kruhové nebo elipsovité oblasti. Chcete-li dosáhnout tohoto chování, můžete umístit `InCircle` funkci do implementace ovládacího prvku (. CPP):

[!code-cpp[NVC_MFC_AxUI#11](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_5.cpp)]

Také budete muset přidat následující deklaraci `InCircle` funkce do hlavičky ovládacího prvku (. H) soubor:

[!code-cpp[NVC_MFC_AxUI#12](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_6.h)]

##  <a name="_core_custom_events_with_stock_names"></a>Vlastní události s názvy akcií

Můžete vytvořit vlastní události se stejným názvem jako s uloženými událostmi, ale nelze je implementovat ve stejném ovládacím prvku. Můžete například chtít vytvořit vlastní událost s názvem kliknout, která se neaktivuje, když by se událost akcie normálně aktivovala. Událost Click pak můžete vyvolat kdykoli voláním funkce vypálení.

Následující postup přidá vlastní událost kliknutí.

#### <a name="to-add-a-custom-event-that-uses-a-stock-event-name"></a>Přidání vlastní události, která používá název uložené události

1. Načtěte projekt ovládacího prvku.

1. V **zobrazení tříd**klikněte pravým tlačítkem myši na třídu ovládacího prvku ActiveX a otevřete místní nabídku.

1. V místní nabídce klikněte na **Přidat** a pak klikněte na **Přidat událost**.

   Tím se otevře Průvodce přidáním události.

1. V rozevíracím seznamu **název události** vyberte uložený název události. V tomto příkladu vyberte **možnost kliknout**.

1. Jako **Typ události**vyberte **vlastní**.

1. Kliknutím na tlačítko **Dokončit** Vytvořte událost.

1. Zavolejte `FireClick` na vhodné místo v kódu.

## <a name="see-also"></a>Viz také:

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)<br/>
[MFC – ovládací prvky ActiveX: Metody](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl – třída](../mfc/reference/colecontrol-class.md)

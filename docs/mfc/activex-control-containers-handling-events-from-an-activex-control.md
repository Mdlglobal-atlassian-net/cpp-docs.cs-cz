---
title: 'ActiveX – kontejnery ovládacích prvků: Zpracování událostí z ovládacího prvku ActiveX'
ms.date: 09/12/2018
helpviewer_keywords:
- event handlers [MFC], ActiveX controls
- ActiveX control containers [MFC], event sinks
- event handling [MFC], ActiveX controls
- ON_EVENT macro [MFC]
- ActiveX controls [MFC], events [MFC]
- END_EVENTSINK_MAP macro, using
- events [MFC], ActiveX controls
- BEGIN_EVENTSINK_MAP macro
ms.assetid: f9c106db-052f-4e32-82ad-750646aa760b
ms.openlocfilehash: 7487792fbc9fe6775640f40755a7f725543fb9f3
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907763"
---
# <a name="activex-control-containers-handling-events-from-an-activex-control"></a>ActiveX – kontejnery ovládacích prvků: Zpracování událostí z ovládacího prvku ActiveX

Tento článek pojednává o použití okna **vlastností** (v **zobrazení tříd**) k instalaci obslužných rutin událostí pro ovládací prvky ActiveX v kontejneru ovládacího prvku ActiveX. Obslužné rutiny události se používají k přijímání oznámení (z ovládacího prvku) určitých událostí a k provedení určité akce v reakci. Toto oznámení se nazývá "vyvolávání" události.

>[!IMPORTANT]
> ActiveX je starší verze technologie, která by se neměla používat pro nový vývoj. Další informace o moderních technologiích, které nahrazují prvky ActiveX, naleznete v tématu [ovládací prvky ActiveX](activex-controls.md).

> [!NOTE]
>  V tomto článku se používá projekt kontejneru ovládacího prvku ActiveX s názvem kontejner a vložený ovládací prvek s názvem circ jako příklady v postupech a kódu.

Pomocí tlačítka události v okně **vlastnosti** (v **zobrazení tříd**) můžete vytvořit mapu událostí, ke kterým může dojít v aplikaci kontejneru ovládacího prvku ActiveX. Tato mapa, označovaná jako "mapa jímky událostí", je vytvořena a spravována jazykem C++ Visual při přidávání obslužných rutin událostí do třídy kontejneru ovládacího prvku. Každá obslužná rutina události, která je implementována pomocí položky mapování události, mapuje konkrétní událost na členskou funkci obslužné rutiny události kontejneru. Tato funkce obslužné rutiny události je volána, když je zadaná událost vyvolána objektem ovládacího prvku ActiveX.

Další informace o mapách jímky událostí najdete v tématu [mapy jímky událostí](../mfc/reference/event-sink-maps.md) v *referenční dokumentaci knihovny tříd*.

##  <a name="_core_event_handler_modifications_to_the_project"></a>Změny obslužné rutiny událostí v projektu

Při použití okna **vlastnosti** pro přidání obslužných rutin událostí je mapa jímky událostí deklarována a definována v projektu. Následující příkazy jsou přidány do ovládacího prvku. Soubor CPP při prvním přidání obslužné rutiny události Tento kód deklaruje mapu jímky událostí pro třídu dialogového okna (v tomto případě `CContainerDlg`):

[!code-cpp[NVC_MFC_AxCont#8](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_1.cpp)]
[!code-cpp[NVC_MFC_AxCont#9](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_2.cpp)]

Při použití okna **vlastnosti** k přidání událostí se do mapy jímky událostí přidá položka (`ON_EVENT`) mapa události a do implementace kontejneru se přidá funkce obslužné rutiny události (. CPP).

Následující příklad deklaruje obslužnou rutinu události, která je `OnClickInCircCtrl`volána pro `ClickIn` událost ovládacího prvku str:

[!code-cpp[NVC_MFC_AxCont#10](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_3.cpp)]

Kromě toho je do `CContainerDlg` implementace třídy přidána následující šablona (. CPP) pro členskou funkci obslužné rutiny události:

[!code-cpp[NVC_MFC_AxCont#11](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_4.cpp)]

Další informace o makrech jímky událostí naleznete v tématu [mapy jímky událostí](../mfc/reference/event-sink-maps.md) v *Referenci knihovny tříd*.

#### <a name="to-create-an-event-handler-function"></a>Vytvoření funkce obslužné rutiny událostí

1. Z Zobrazení tříd vyberte třídu dialogového okna, která obsahuje ovládací prvek ActiveX. V tomto příkladu použijte `CContainerDlg`.

1. V okně **vlastnosti** klikněte na tlačítko **události** .

1. V okně **vlastnosti** vyberte ID ovládacího prvku vloženého ovládacího prvku ActiveX. V tomto příkladu použijte `IDC_CIRCCTRL1`.

   V okně **vlastnosti** se zobrazí seznam událostí, které mohou být aktivovány integrovaným ovládacím prvkem ActiveX. Žádná členská funkce zobrazená tučně již má přiřazené obslužné rutiny.

1. Vyberte událost, kterou má třída dialogového okna zpracovat. V tomto příkladu vyberte **možnost kliknout**.

1. V rozevíracím seznamu na pravé straně vyberte  **\<přidat > ClickCircctrl1**.

1. Dvojím kliknutím na novou funkci obslužné rutiny z Zobrazení tříd přejděte na kód obslužné rutiny události v implementaci (. CPP) souboru `CContainerDlg`.

## <a name="see-also"></a>Viz také:

[ActiveX – kontejnery ovládacích prvků](../mfc/activex-control-containers.md)

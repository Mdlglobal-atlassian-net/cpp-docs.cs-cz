---
title: 'ActiveX – kontejnery ovládacích prvků: Ošetření událostí v ovládacím prvku ActiveX'
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
ms.openlocfilehash: ae623ee0973e78db3b542646dd6bdec58cc2dfc8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367956"
---
# <a name="activex-control-containers-handling-events-from-an-activex-control"></a>ActiveX – kontejnery ovládacích prvků: Ošetření událostí v ovládacím prvku ActiveX

Tento článek popisuje použití okna **Vlastnosti** (v **zobrazení tříd )** k instalaci obslužných rutin událostí pro ovládací prvky ActiveX v kontejneru ovládacích prvků ActiveX. Obslužné rutiny událostí se používají k přijímání oznámení (z ovládacího prvku) určitých událostí a provést některé akce v reakci. Toto oznámení se nazývá "spouštění" události.

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být použita pro nový vývoj. Další informace o moderních technologiích, které nahrazují ovládací prvky ActiveX, naleznete [v tématu ActiveX Controls](activex-controls.md).

> [!NOTE]
> Tento článek používá projekt kontejneru ovládacího prvku ActiveX založený na dialogu s názvem Kontejner a vložený ovládací prvek s názvem Circ jako příklady v postupech a kódu.

Pomocí tlačítka Události v okně **Vlastnosti** (v **zobrazení tříd )** můžete vytvořit mapu událostí, ke kterým může dojít v aplikaci kontejneru ovládacího prvku ActiveX. Tato mapa, nazývaná "mapa jímky událostí", je vytvořena a udržována visual c++ při přidání obslužných rutin událostí do třídy kontejneru ovládacího prvku. Každá obslužná rutina události, implementovaná s položkou mapy událostí, mapuje konkrétní událost na členskou funkci obslužné rutiny události kontejneru. Tato funkce obslužné rutiny události je volána, když je zadaná událost aktivována objektem ovládacího prvku ActiveX.

Další informace o mapách jímky událostí najdete v tématu [Mapy jímky událostí](../mfc/reference/event-sink-maps.md) v *referenční knihovně tříd*.

## <a name="event-handler-modifications-to-the-project"></a><a name="_core_event_handler_modifications_to_the_project"></a>Úpravy obslužné rutiny událostí v projektu

Při použití okna **Vlastnosti** přidat obslužné rutiny událostí, mapa jímky událostí je deklarována a definována v projektu. Následující příkazy jsou přidány do ovládacího prvku . CPP při prvním přidání obslužné rutiny události. Tento kód deklaruje mapu jímky událostí pro `CContainerDlg`třídu dialogového okna (v tomto případě ):

[!code-cpp[NVC_MFC_AxCont#8](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_1.cpp)]
[!code-cpp[NVC_MFC_AxCont#9](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_2.cpp)]

Při použití okna **Vlastnosti** k přidání událostí`ON_EVENT`je do mapy jímky událostí přidána položka mapy událostí a do implementace kontejneru (. CPP).

Následující příklad deklaruje `OnClickInCircCtrl`obslužnou rutinu `ClickIn` události, volanou pro událost ovládacího prvku Circ:

[!code-cpp[NVC_MFC_AxCont#10](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_3.cpp)]

Kromě toho je do implementace `CContainerDlg` třídy přidána následující šablona (. CPP) pro členovou funkci obslužné rutiny události:

[!code-cpp[NVC_MFC_AxCont#11](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_4.cpp)]

Další informace o makra jímky událostí naleznete v tématu [Mapy jímky událostí](../mfc/reference/event-sink-maps.md) v *odkaz na knihovnu tříd*.

#### <a name="to-create-an-event-handler-function"></a>Vytvoření funkce obslužné rutiny události

1. Ze zobrazení tříd vyberte třídu dialogu, která obsahuje ovládací prvek ActiveX. V tomto příkladu použijte `CContainerDlg`.

1. V okně **Vlastnosti** klepněte na tlačítko **Události.**

1. V okně **Vlastnosti** vyberte ID ovládacího prvku vloženého ovládacího prvku ActiveX. V tomto příkladu použijte `IDC_CIRCCTRL1`.

   Okno **Vlastnosti** zobrazuje seznam událostí, které mohou být aktivovány vloženým ovládacím prvkem ActiveX. Všechny členské funkce zobrazené tučně již má přiřazeny funkce obslužné rutiny.

1. Vyberte událost, kterou má třída dialogu zpracovat. V tomto příkladu vyberte **Klepněte na**tlačítko .

1. V rozevíracím seznamu vpravo vyberte ** \<Přidat> ClickCircctrl1**.

1. Poklepáním na novou funkci obslužné rutiny ze zobrazení třídy přejděte na kód obslužné rutiny události v implementaci (. CPP) soubor `CContainerDlg`.

## <a name="see-also"></a>Viz také

[ActiveX – kontejnery ovládacích prvků](../mfc/activex-control-containers.md)

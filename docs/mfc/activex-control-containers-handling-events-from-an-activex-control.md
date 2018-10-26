---
title: '– Kontejnery ovládacích prvků ActiveX: Ošetření událostí ovládacího prvku ActiveX | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 913bc04533668e6576a84641937992504f49390a
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50080075"
---
# <a name="activex-control-containers-handling-events-from-an-activex-control"></a>ActiveX – kontejnery ovládacích prvků: Ošetření událostí v ovládacím prvku ActiveX

Tento článek popisuje, v okně Vlastnosti instalace obslužné rutiny událostí pro ovládací prvky ActiveX v kontejneru ovládacího prvku ActiveX. Obslužné rutiny událostí slouží k přijímání oznámení (z ovládacího prvku) o určité události a provést některé akce v odpovědi. Toto oznámení se nazývá "vyvoláním" události.

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být používána při novém vývoji. Další informace o moderních technologií, které nahrazují ActiveX naleznete v tématu [ovládací prvky ActiveX](activex-controls.md).

> [!NOTE]
>  Tento článek používá založené na dialogu ActiveX ovládací prvek kontejneru projekt s názvem kontejneru a vloženému ovládacímu prvku s názvem KR jako příklady v procedurách a kódu.

Pomocí tlačítka události v okně Vlastnosti, můžete vytvořit mapu událostí, ke kterým může dojít v vaše kontejnerové aplikace ovládacího prvku ActiveX. Toto mapování, nazývá "událostí jímky mapa," se vytvářejí a udržují Visual C++ při přidání obslužné rutiny událostí na třídě ovládacího prvku kontejneru. Každá obslužná rutina události, implementuje pomocí položka mapy událostí mapuje na členskou funkci obslužné rutiny události kontejneru určité události. Tato funkce obslužnou rutinu události je volána, když zadanou událost se aktivuje v objektu ovládacího prvku ActiveX.

Další informace o mapy jímek událostí najdete v tématu [mapy jímek událostí](../mfc/reference/event-sink-maps.md) v *knihovny tříd*.

##  <a name="_core_event_handler_modifications_to_the_project"></a> Úpravy obslužné rutiny událostí do projektu

Použijete-li přidat obslužné rutiny událostí v okně Vlastnosti, mapu jímky událostí je deklarovány a definovány ve vašem projektu. Následující příkazy jsou přidány do ovládacího prvku. Soubor CPP při prvním přidání obslužné rutiny události. Tento kód deklaruje mapu událostí jímky pro třídy dialogového okna (v tomto případě `CContainerDlg`):

[!code-cpp[NVC_MFC_AxCont#8](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_1.cpp)]
[!code-cpp[NVC_MFC_AxCont#9](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_2.cpp)]

Použijte okno Vlastnosti pro přidání události, události namapovat záznam (`ON_EVENT`) se přidá na mapě událostí jímky a obslužné rutiny události funkce se přidá do kontejneru implementace (. Soubor CPP).

Následující příklad deklaruje obslužnou rutinu události, volá `OnClickInCircCtrl`, pro ovládací prvek KR `ClickIn` události:

[!code-cpp[NVC_MFC_AxCont#10](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_3.cpp)]

Navíc následující šablona se přidá do `CContainerDlg` implementace třídy (. Soubor CPP) pro členské funkce obslužné rutiny události:

[!code-cpp[NVC_MFC_AxCont#11](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_4.cpp)]

Další informace o makra jímky událostí, naleznete v tématu [mapy jímek událostí](../mfc/reference/event-sink-maps.md) v *knihovny tříd*.

#### <a name="to-create-an-event-handler-function"></a>Chcete-li vytvořit funkci obslužné rutiny událostí

1. Zobrazení tříd vyberte třídy dialogového okna, která obsahuje ovládací prvek ActiveX. V tomto příkladu použijte `CContainerDlg`.

1. V okně Vlastnosti klikněte na tlačítko **události** tlačítko.

1. V okně Vlastnosti vyberte ID ovládacího prvku vloženému ovládacímu prvku ActiveX. V tomto příkladu použijte `IDC_CIRCCTRL1`.

   V okně Vlastnosti se zobrazí seznam událostí, které mohou být vyvolané vloženému ovládacímu prvku ActiveX. Žádnou členskou funkci zobrazeny tučně už má přiřazenou funkce obslužné rutiny.

1. Vyberte událost má třídy dialogového okna pro zpracování. V tomto příkladu vyberte **klikněte na tlačítko**.

1. Z rozevíracího seznamu na pravé straně vyberte  **\<Přidat > ClickCircctrl1**.

1. Dvakrát klikněte na novou funkci obslužné rutiny ze zobrazení tříd pro přechod na kód obslužné rutiny událostí v implementaci (. Soubor CPP) `CContainerDlg`.

## <a name="see-also"></a>Viz také

[ActiveX – kontejnery ovládacích prvků](../mfc/activex-control-containers.md)


---
title: "– Kontejnery ovládacích prvků ActiveX: Ošetření událostí v ovládacím prvku ActiveX | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 84e1571f400297584e12a40dfd2bfcc3c0b525d2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="activex-control-containers-handling-events-from-an-activex-control"></a>ActiveX – kontejnery ovládacích prvků: Ošetření událostí v ovládacím prvku ActiveX
Tento článek popisuje pomocí okna vlastnosti instalace obslužných rutin událostí pro ovládací prvky ActiveX v kontejneru ovládacího prvku ActiveX. Obslužné rutiny událostí se používají k přijímání oznámení (z ovládacího prvku) určité události a provedení několika akcí v odpovědi. Toto oznámení se nazývá "ohlásí" události.  
  
> [!NOTE]
>  Tento článek používá na základě dialogové okno ActiveX řízení kontejneru projekt s názvem kontejneru a vloženému ovládacímu prvku s názvem str jako příklady v postupy a kódu.  
  
 Pomocí tlačítka události v okně vlastností, můžete vytvořit mapu událostí, které můžou nastat ve vaší aplikaci kontejneru ovládacího prvku ActiveX. Tato mapa nazývá "události podřízený mapa,'' je vytvářené a udržované pomocí Visual C++ při přidání obslužné rutiny událostí k třídě ovládacího prvku kontejneru. Každý obslužná rutina události, implementovaný pomocí položku mapy událostí mapuje konkrétní události členské funkce kontejneru událost obslužné rutiny. Tato funkce obslužné rutiny událostí je volána, když zadanou událost je aktivována například objekt ovládacího prvku ActiveX.  
  
 Další informace o mapy jímek událostí najdete v tématu [mapy jímek událostí](../mfc/reference/event-sink-maps.md) v *knihovny tříd*.  
  
##  <a name="_core_event_handler_modifications_to_the_project"></a>Obslužná rutina události změny v projektu  
 Použijete-li vlastnosti – okno pro přidání obslužné rutiny událostí, mapy jímek událostí je deklarovaný a definované ve vašem projektu. Následující příkazy se přidají do ovládacího prvku. Soubor CPP při prvním přidání obslužné rutiny události. Tento kód deklaruje mapou události jímku pro třídy dialogového okna (v tomto případě `CContainerDlg`):  
  
 [!code-cpp[NVC_MFC_AxCont#8](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_1.cpp)]  
[!code-cpp[NVC_MFC_AxCont#9](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_2.cpp)]  
  
 Jako okno Vlastnosti použít pro přidání události, událost mapování položka (`ON_EVENT`) je přidána mapy jímek událostí a obslužné rutiny události se přidá funkce pro implementaci kontejneru (. Soubor CPP).  
  
 Následující příklad deklaruje obslužnou rutinu události volat `OnClickInCircCtrl`, pro ovládací prvek str **clickin –** událostí:  
  
 [!code-cpp[NVC_MFC_AxCont#10](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_3.cpp)]  
  
 Kromě toho je do následující šablony `CContainerDlg` implementaci třídy (. Soubor CPP) pro členské funkce obslužné rutiny událostí:  
  
 [!code-cpp[NVC_MFC_AxCont#11](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_4.cpp)]  
  
 Další informace o makra jímky událostí najdete v tématu [mapy jímek událostí](../mfc/reference/event-sink-maps.md) v *knihovny tříd*.  
  
#### <a name="to-create-an-event-handler-function"></a>Chcete-li vytvořit funkci zpracování událostí  
  
1.  Zobrazení tříd vyberte třídy dialogového okna, který obsahuje ovládací prvek ActiveX. V tomto příkladu použijte `CContainerDlg`.  
  
2.  V okně vlastností klikněte **události** tlačítko.  
  
3.  V okně vlastností vyberte ID ovládacího prvku embedded ovládacího prvku ActiveX. V tomto příkladu použijte `IDC_CIRCCTRL1`.  
  
     V okně Vlastnosti se zobrazí seznam událostí, které může být aktivována embedded ovládací prvek ActiveX. Všechny funkce člen zobrazeny tučně již má přiřazen funkce obslužných rutin.  
  
4.  Vyberte události chcete třídy dialogového okna pro zpracování. V tomto příkladu vyberte **klikněte na tlačítko**.  
  
5.  Z rozevíracího seznamu na pravé straně, vyberte  **\<Přidat > ClickCircctrl1**.  
  
6.  Dvakrát klikněte na nové funkce obslužné rutiny ze zobrazení tříd pro přechod na kód obslužné rutiny událostí v implementaci (. Soubor CPP) `CContainerDlg`.  
  
## <a name="see-also"></a>Viz také  
 [ActiveX – kontejnery ovládacích prvků](../mfc/activex-control-containers.md)


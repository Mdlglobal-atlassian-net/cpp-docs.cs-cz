---
title: Příjem oznámení z běžných ovládacích prvků | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- ON_NOTIFY
- WM_NOTIFY
dev_langs:
- C++
helpviewer_keywords:
- OnNotify method [MFC]
- common controls [MFC], notifications
- ON_NOTIFY macro [MFC]
- controls [MFC], notifications
- receiving notifications from common controls
- notifications [MFC], common controls
- Windows common controls [MFC], notifications
- WM_NOTIFY message
ms.assetid: 50194592-d60d-44d0-8ab3-338a2a2c63e7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 30e89c8d25d78477ed98bae0fd06a704e32d3906
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349710"
---
# <a name="receiving-notification-from-common-controls"></a>Příjem oznámení z běžných ovládacích prvků
Běžné ovládací prvky jsou podřízená okna, které odesílají zprávy s oznámením do nadřazeného okna, když dojde k události, jako je vstup od uživatele, v ovládacím prvku.  
  
 Aplikace spoléhá na tyto zprávy oznámení a určete, jaká opatření se chce uživatel k provedení. Většina běžných ovládacích prvků zasílání oznámení, jako **wm_notify –** zprávy. Ovládací prvky Windows odeslat většina zpráv s oznámením jako **wm_command –** zprávy. [CWnd::OnNotify](../mfc/reference/cwnd-class.md#onnotify) je obslužná rutina pro **wm_notify –** zprávy. Stejně jako u `CWnd::OnCommand`, provádění `OnNotify` odešle zprávu oznámení k `OnCmdMsg` pro zpracování v mapy zpráv. Položka mapy zpráv pro zpracování oznámení je `ON_NOTIFY`. Další informace najdete v tématu [technické 61 Poznámka: ON_NOTIFY a wm_notify – zprávy](../mfc/tn061-on-notify-and-wm-notify-messages.md).  
  
 Alternativně můžete do odvozené třídy zpracování vlastní zprávy oznámení pomocí "reflexe zpráv." Další informace najdete v tématu [technické 62 Poznámka: reflexe zprávy pro Windows prvky](../mfc/tn062-message-reflection-for-windows-controls.md).  
  
## <a name="retrieving-the-cursor-position-in-a-notification-message"></a>Načítání pozice kurzoru v oznámení  
 V některých případech je užitečné pro určení aktuální pozice kurzoru, kdy některé zprávy oznámení jsou přijímány běžného ovládacího prvku. Například by být užitečné k určení aktuální umístění kurzoru, když obdrží běžného ovládacího prvku **nm_rclick –** oznámení.  
  
 Je jednoduchý způsob, jak dosáhnout voláním `CWnd::GetCurrentMessage`. Tato metoda však pouze načte pozice kurzoru v době, kdy byla zpráva odeslána. Protože kurzor byl pravděpodobně přesunut vzhledem k tomu, že zpráva byla odeslána musí volat **CWnd::GetCursorPos** získat aktuální pozici kurzoru.  
  
> [!NOTE]
>  `CWnd::GetCurrentMessage` by měla být volána pouze v rámci obslužné rutiny zpráv.  
  
 Přidejte následující kód k tělu obslužné rutiny zpráv oznámení (v tomto příkladu **nm_rclick –**):  
  
 [!code-cpp[NVC_MFCControlLadenDialog#4](../mfc/codesnippet/cpp/receiving-notification-from-common-controls_1.cpp)]  
  
 V tomto okamžiku je uložen umístění ukazatele myši v `cursorPos` objektu.  
  
## <a name="see-also"></a>Viz také  
 [Příprava a použití ovládacích prvků](../mfc/making-and-using-controls.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)


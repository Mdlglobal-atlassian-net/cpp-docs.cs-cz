---
title: Příjem oznámení z běžných ovládacích prvků | Dokumentace Microsoftu
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
ms.openlocfilehash: 25979ec1157a4d2beedf96875e6c8c270b3aaaa9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442380"
---
# <a name="receiving-notification-from-common-controls"></a>Příjem oznámení z běžných ovládacích prvků

Běžné ovládací prvky jsou podřízených oken, které odesílají zprávy oznámení nadřazenému oknu, když dojde k události, jako je například vstup od uživatele, v ovládacím prvku.

Aplikace se spoléhá na tyto zprávy oznámení a zjistěte, jakou akci uživatel chce, aby se k provedení. Většina běžných ovládacích prvků zasílání oznámení, jako wm_notify – zprávy. Ovládací prvky Windows většina zpráv s oznámením odeslat jako wm_command – zprávy. [CWnd::OnNotify](../mfc/reference/cwnd-class.md#onnotify) je obslužná rutina wm_notify – zprávy. Stejně jako u `CWnd::OnCommand`, provádění `OnNotify` odešle zprávu do zprávu s oznámením `OnCmdMsg` pro zpracování v mapování zprávy. Položka mapování zpráv pro zpracování oznámení o je ON_NOTIFY. Další informace najdete v tématu [Technická poznámka 61: ON_NOTIFY a wm_notify – zprávy](../mfc/tn061-on-notify-and-wm-notify-messages.md).

Alternativně odvozená třída může zpracovávat své vlastní zprávy oznámení pomocí "reflexe zprávy." Další informace najdete v tématu [62 technická Poznámka: reflexe zprávy pro Windows prvky](../mfc/tn062-message-reflection-for-windows-controls.md).

## <a name="retrieving-the-cursor-position-in-a-notification-message"></a>Načítání pozice kurzoru v zprávu s oznámením

V některých případech je užitečné určit aktuální pozici kurzoru, kdy některé zprávy oznámení jsou přijímány běžného ovládacího prvku. Například by být užitečná k určení aktuální umístění kurzoru, když běžný ovládací prvek dostane zprávu nm_rclick – oznámení.

Neexistuje jednoduchý způsob, jak to provést pomocí volání `CWnd::GetCurrentMessage`. Tato metoda však pouze načte pozici kurzoru v době, kdy byla zpráva odeslána. Protože kurzor byl pravděpodobně přesunut od odeslání zprávy je nutné volat `CWnd::GetCursorPos` zobrazíte aktuální pozici kurzoru.

> [!NOTE]
>  `CWnd::GetCurrentMessage` by měla být volána pouze v rámci obslužné rutiny zpráv.

Přidejte následující kód do těla obslužné rutiny zprávy oznámení (v tomto příkladu nm_rclick –):

[!code-cpp[NVC_MFCControlLadenDialog#4](../mfc/codesnippet/cpp/receiving-notification-from-common-controls_1.cpp)]

V tomto okamžiku je umístění kurzoru myši uložené v `cursorPos` objektu.

## <a name="see-also"></a>Viz také

[Příprava a použití ovládacích prvků](../mfc/making-and-using-controls.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)


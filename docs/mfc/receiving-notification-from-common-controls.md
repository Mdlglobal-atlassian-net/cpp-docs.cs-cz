---
title: Příjem oznámení z běžných ovládacích prvků
ms.date: 11/04/2016
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
ms.openlocfilehash: 73315d4a1107204bc6adc885729fdeeaeb7f98d0
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298971"
---
# <a name="receiving-notification-from-common-controls"></a>Příjem oznámení z běžných ovládacích prvků

Běžné ovládací prvky jsou podřízená okna, která odesílají oznamovací zprávy do nadřazeného okna, když v ovládacím prvku dojde k událostem, jako je například vstup od uživatele.

Aplikace spoléhá na tyto oznamovací zprávy a určí, jakou akci uživatel chce provést. Nejběžnější ovládací prvky odesílají oznamovací zprávy jako WM_NOTIFY zprávy. Ovládací prvky Windows odesílají většinu oznamovacích zpráv jako WM_COMMAND zprávy. [CWnd:: s upozorněním](../mfc/reference/cwnd-class.md#onnotify) je obslužná rutina zprávy WM_NOTIFY. Stejně jako u `CWnd::OnCommand`, implementace `OnNotify` odešle zprávu oznámení do `OnCmdMsg` pro zpracování v mapách zpráv. Položka mapování zpráv pro zpracování oznámení je ON_NOTIFY. Další informace najdete v tématu [Technická poznámka 61: ON_NOTIFY a WM_NOTIFY zprávy](../mfc/tn061-on-notify-and-wm-notify-messages.md).

Alternativně může odvozená třída zpracovávat své vlastní oznamovací zprávy pomocí příkazu "reflexe zprávy". Další informace naleznete v části [Technická poznámka 62: reflexe zprávy pro ovládací prvky systému Windows](../mfc/tn062-message-reflection-for-windows-controls.md).

## <a name="retrieving-the-cursor-position-in-a-notification-message"></a>Načítání pozice kurzoru v oznamovací zprávě

V některých případech je vhodné určit aktuální pozici kurzoru, pokud jsou určité zprávy oznámení přijímány běžným ovládacím prvkem. Například by bylo užitečné určit aktuální umístění kurzoru, když běžný ovládací prvek obdrží zprávu NM_RCLICK oznámení.

Existuje jednoduchý způsob, jak to provést voláním `CWnd::GetCurrentMessage`. Tato metoda však v okamžiku odeslání zprávy pouze načte pozici kurzoru. Vzhledem k tomu, že se kurzor mohl přesunout od odeslání zprávy, je nutné volat `CWnd::GetCursorPos` pro získání aktuální pozice kurzoru.

> [!NOTE]
>  `CWnd::GetCurrentMessage` by měla být volána pouze v rámci obslužné rutiny zprávy.

Do těla obslužné rutiny zprávy s oznámením přidejte následující kód (v tomto příkladu NM_RCLICK):

[!code-cpp[NVC_MFCControlLadenDialog#4](../mfc/codesnippet/cpp/receiving-notification-from-common-controls_1.cpp)]

V tomto okamžiku je umístění kurzoru myši Uloženo v objektu `cursorPos`.

## <a name="see-also"></a>Viz také:

[Příprava a použití ovládacích prvků](../mfc/making-and-using-controls.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

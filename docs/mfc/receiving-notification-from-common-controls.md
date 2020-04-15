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
ms.openlocfilehash: 9205facb5ec4e2491308020d9667a27ab8deb96b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371786"
---
# <a name="receiving-notification-from-common-controls"></a>Příjem oznámení z běžných ovládacích prvků

Běžné ovládací prvky jsou podřízená okna, která odesílají oznámení do nadřazeného okna, když dojde k událostem, jako je například vstup od uživatele, v ovládacím prvku.

Aplikace spoléhá na tyto zprávy oznámení k určení, jaké akce uživatel chce, aby přijaly. Nejběžnější ovládací prvky odesílají oznámení jako WM_NOTIFY zprávy. Ovládací prvky systému Windows odesílají většinu oznámení jako WM_COMMAND zpráv. [CWnd::OnNotify](../mfc/reference/cwnd-class.md#onnotify) je obslužná rutina zprávy WM_NOTIFY. Stejně `CWnd::OnCommand`jako u `OnNotify` , provádění odešle oznámení pro `OnCmdMsg` zpracování v mapách zpráv. Položka mapy zpráv pro zpracování oznámení je ON_NOTIFY. Další informace naleznete [v technické poznámce 61: ON_NOTIFY a WM_NOTIFY zprávy](../mfc/tn061-on-notify-and-wm-notify-messages.md).

Odvozené třídy může zpracovávat vlastní oznámení pomocí "odraz zprávy." Další informace naleznete [v technické poznámce 62: Reflexe zpráv pro ovládací prvky systému Windows](../mfc/tn062-message-reflection-for-windows-controls.md).

## <a name="retrieving-the-cursor-position-in-a-notification-message"></a>Načítání pozice kurzoru v oznamovací zprávě

V některých případech je užitečné určit aktuální pozici kurzoru, když jsou určité oznámení přijata společným ovládacím prvkem. Například by bylo užitečné určit aktuální umístění kurzoru, když společný ovládací prvek obdrží NM_RCLICK oznámení.

Existuje jednoduchý způsob, jak toho `CWnd::GetCurrentMessage`dosáhnout voláním . Tato metoda však načte pouze pozici kurzoru v době, kdy byla zpráva odeslána. Vzhledem k tomu, že kurzor byl `CWnd::GetCursorPos` pravděpodobně přesunut od odeslání zprávy, musíte volat, abyste získali aktuální pozici kurzoru.

> [!NOTE]
> `CWnd::GetCurrentMessage`by měla být volána pouze v rámci obslužné rutiny zprávy.

Přidejte následující kód do těla obslužné rutiny zprávy oznámení (v tomto příkladu NM_RCLICK):

[!code-cpp[NVC_MFCControlLadenDialog#4](../mfc/codesnippet/cpp/receiving-notification-from-common-controls_1.cpp)]

V tomto okamžiku je umístění kurzoru myši uloženy v objektu. `cursorPos`

## <a name="see-also"></a>Viz také

[Příprava a použití ovládacích prvků](../mfc/making-and-using-controls.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

---
title: Zpracování a mapování zpráv
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, messages
- message handling [MFC]
- message maps [MFC]
ms.assetid: 62fe2a1b-944c-449d-a0f0-63c11ee0a3cb
ms.openlocfilehash: 0321d98d8b92af0b80259bc49e84e69b987577a4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508245"
---
# <a name="message-handling-and-mapping"></a>Zpracování a mapování zpráv

Tento článek popisuje, jak jsou zprávy a příkazy zpracovávány rozhraním MFC a jak je připojit ke svým obslužným funkcím.

V tradičních programech pro systém Windows se zprávy systému Windows zpracovávají v rámci velkého příkazu switch v proceduře okna. Knihovna MFC místo toho používá [mapy zpráv](../mfc/message-categories.md) k mapování přímých zpráv na samostatné členské funkce třídy. Mapy zpráv jsou pro tento účel efektivnější než virtuální funkce a umožňují zpracování zpráv nejvhodnějším C++ objektem – aplikací, dokumentem, zobrazením a tak dále. Můžete namapovat jednu zprávu nebo rozsah zpráv, ID příkazů nebo ID ovládacích prvků.

WM_COMMAND zprávy (obvykle generované nabídkami, tlačítky na panelu nástrojů nebo akcelerátory) používají také mechanismus mapování zpráv. Knihovna MFC definuje standardní [Směrování](../mfc/command-routing.md) zpráv příkazů mezi aplikací, oknem rámců, zobrazením a aktivními dokumenty v programu. V případě potřeby můžete toto směrování přepsat.

Mapy zpráv také poskytují způsob, jak aktualizovat objekty uživatelského rozhraní (například nabídky a tlačítka panelu nástrojů), povolit nebo zakázat, aby vyhovovaly aktuálnímu kontextu.

Obecné informace o zprávách a frontách zpráv v systému Windows najdete v tématu [zprávy a fronty zpráv](/windows/win32/winmsg/messages-and-message-queues) v Windows SDK.

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace

- [Zprávy a příkazy v prostředí .NET Framework](../mfc/messages-and-commands-in-the-framework.md)

- [Způsob, jakým rozhraní volá obslužnou rutinu zprávy](../mfc/how-the-framework-calls-a-handler.md)

- [Jak framework prohledává mapy zpráv](../mfc/how-the-framework-searches-message-maps.md)

- [Deklarace funkcí obslužných rutin zpráv](../mfc/declaring-message-handler-functions.md)

- [Mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md)

- [Postup zobrazení informací o příkazu ve stavovém řádku](../mfc/how-to-display-command-information-in-the-status-bar.md)

- [Dynamická aktualizace objektů uživatelského rozhraní](../mfc/how-to-update-user-interface-objects.md)

- [Postupy: Vytvoření mapy zpráv pro třídu šablony](../mfc/how-to-create-a-message-map-for-a-template-class.md)

## <a name="see-also"></a>Viz také:

[Charakteristiky](../mfc/mfc-concepts.md)<br/>
[Obecná témata MFC](../mfc/general-mfc-topics.md)<br/>
[CWnd – třída](../mfc/reference/cwnd-class.md)<br/>
[CCmdTarget – třída](../mfc/reference/ccmdtarget-class.md)

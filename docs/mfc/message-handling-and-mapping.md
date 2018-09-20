---
title: Zpracování a mapování zpráv | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, messages
- message handling [MFC]
- message maps [MFC]
ms.assetid: 62fe2a1b-944c-449d-a0f0-63c11ee0a3cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b8c0fc3b9eec88fc9db9bb4eaff93381d1368368
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444317"
---
# <a name="message-handling-and-mapping"></a>Zpracování a mapování zpráv

Řada Tento článek popisuje způsob zpracování zprávy a příkazy v rámci rozhraní knihovny MFC a způsob jejich připojení k příslušným obslužným funkcím.

Tradiční aplikace pro Windows Windows zprávy jsou zpracovány v příkazu switch velké v proceduru okna. Knihovna MFC používá místo toho [zprávy maps](../mfc/message-categories.md) k mapování přímé zprávy na členské funkce různých tříd. Mapy zpráv jsou účinnější než virtuální funkce pro tento účel a umožňují zprávy zpracovávat nejvhodnější objekt jazyka C++ – aplikace, dokumentu, zobrazení a tak dále. Můžete mapovat do jedné zprávy nebo zprávy, ID příkazů rozsah nebo ovládací prvek ID.

Wm_command – zprávy – obvykle generovaných nabídek, tlačítek panelu nástrojů nebo akcelerátory – také použití mechanismu mapování zprávy. MFC definuje standardní [směrování](../mfc/command-routing.md) příkaz zpráv mezi aplikace, rámec okna, zobrazení a aktivní dokumenty v programu. Můžete přepsat, toto směrování, pokud je potřeba.

Mapy zpráv také zadat způsob aktualizace objektů uživatelského rozhraní (jako jsou nabídky a tlačítka panelu nástrojů), povolení nebo zakázání je tak, aby odpovídaly aktuálním kontextu.

Obecné informace o zprávy a fronty zpráv ve Windows najdete v tématu [zprávy a fronty zpráv](https://msdn.microsoft.com/library/windows/desktop/ms632590) v sadě Windows SDK.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Zprávy a příkazy v prostředí .NET Framework](../mfc/messages-and-commands-in-the-framework.md)

- [Jakým způsobem volá framework obslužné rutiny zpráv](../mfc/how-the-framework-calls-a-handler.md)

- [Jak framework prohledává mapy zpráv](../mfc/how-the-framework-searches-message-maps.md)

- [Deklarace funkcí obslužných rutin zpráv](../mfc/declaring-message-handler-functions.md)

- [Mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md)

- [Postup zobrazení informací o příkazu ve stavovém řádku](../mfc/how-to-display-command-information-in-the-status-bar.md)

- [Dynamická aktualizace objektů uživatelského rozhraní](../mfc/how-to-update-user-interface-objects.md)

- [Postupy: Vytvoření mapy zpráv pro třídu šablony](../mfc/how-to-create-a-message-map-for-a-template-class.md)

## <a name="see-also"></a>Viz také

[Koncepty](../mfc/mfc-concepts.md)<br/>
[Obecná témata MFC](../mfc/general-mfc-topics.md)<br/>
[CWnd – třída](../mfc/reference/cwnd-class.md)<br/>
[CCmdTarget – třída](../mfc/reference/ccmdtarget-class.md)

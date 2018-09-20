---
title: 'Windows Sockets: Odvozování z tříd soketů | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- derived classes [MFC], from socket classes
- Windows Sockets [MFC], deriving from socket classes
- sockets [MFC], deriving from socket classes
ms.assetid: 3a26e67a-e323-433b-9b05-eca018799801
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c562a8d6bf1c3f00f3812f6c25a4afd70276c64f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418954"
---
# <a name="windows-sockets-deriving-from-socket-classes"></a>Windows Sockets: Odvozování z tříd soketů

Tento článek popisuje některé funkce, které můžete získat vlastní třídy odvozené z jednoho z tříd soketů.

Vaše vlastní třídy soketu lze odvodit z buď [CAsyncSocket](../mfc/reference/casyncsocket-class.md) nebo [csocket –](../mfc/reference/csocket-class.md) přidat vlastní funkce. Konkrétně se tyto třídy zadat počet virtuální členské funkce, které můžete přepsat. Tyto funkce patří [události OnReceive](../mfc/reference/casyncsocket-class.md#onreceive), [OnSend](../mfc/reference/casyncsocket-class.md#onsend), [OnAccept](../mfc/reference/casyncsocket-class.md#onaccept), [OnConnect](../mfc/reference/casyncsocket-class.md#onconnect), a [při zavření](../mfc/reference/casyncsocket-class.md#onclose). Funkce můžete přepsat v třídě odvozené soketu výhod oznámení, která poskytují při výskytu události sítě. Rozhraní volá tyto funkce zpětného volání oznámení upozornění na důležité soketu události, jako je například příjem dat, může začínat čtení. Další informace o funkcích notification, najdete v části [rozhraní Windows Sockets: oznámení soketů](../mfc/windows-sockets-socket-notifications.md).

Kromě toho třídy `CSocket` poskytuje [OnMessagePending](../mfc/reference/csocket-class.md#onmessagepending) členská funkce (rozšířené overridable). MFC tuto funkci volá, když soket je – čerpání zpráv založené na Windows. Můžete přepsat `OnMessagePending` vyhledat konkrétní zprávy z Windows a reagovat na ně.

Výchozí verze `OnMessagePending` zadané ve třídě `CSocket` prozkoumá fronty zpráv pro zprávy WM_PAINT při čekání na dokončení blokování volání. Odešle malovat zprávy ke zlepšení kvality zobrazení. Kromě něco užitečné, to ukazuje jeden ze způsobů může přepsat funkci sami. Další příklad, zvažte použití `OnMessagePending` pro následující úlohu. Předpokládejme, že zobrazit dialogové okno nemodální při čekání, k dokončení transakce sítě. Dialogové okno obsahuje tlačítko Storno, které může uživatel použít pro zrušení blokování transakcí, které trvají příliš dlouho. Vaše `OnMessagePending` přepsání může pump zprávy týkající se této nemodální dialogové okno.

Ve vaší `OnMessagePending` přepsat, vrátit buď **TRUE** nebo proveďte návrat z volání základní třídy verzi `OnMessagePending`. Verze základní třídy volání provádí práci, která stále chcete-li.

Další informace naleznete v tématu:

- [Windows Sockets: Použití soketů s archivy](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets – Použití třídy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets: Blokování](../mfc/windows-sockets-blocking.md)

- [Windows Sockets: Pořadí bajtů](../mfc/windows-sockets-byte-ordering.md)

- [Windows Sockets: Převádění řetězců](../mfc/windows-sockets-converting-strings.md)

## <a name="see-also"></a>Viz také

[Windows Sockets v prostředí MFC](../mfc/windows-sockets-in-mfc.md)


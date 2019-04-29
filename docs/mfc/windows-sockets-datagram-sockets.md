---
title: 'Windows Sockets: Sokety datagramu'
ms.date: 11/04/2016
helpviewer_keywords:
- sockets [MFC], datagram
- Windows Sockets [MFC], bi-directional data flow
- datagram sockets [MFC]
- Windows Sockets [MFC], datagram
- sockets [MFC], bi-directional data flow
ms.assetid: bec16a1c-74c0-4ff9-8c18-c2d87897d264
ms.openlocfilehash: 14d33ece66d902b5705e573e9863ea78fff9737f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385283"
---
# <a name="windows-sockets-datagram-sockets"></a>Windows Sockets: Sokety datagramu

Tento článek popisuje sokety datagramu, jeden ze dvou typů Windows Socket, která je k dispozici. (Je typ [stream soketu](../mfc/windows-sockets-stream-sockets.md).)

Sokety datagramu podporují datový tok obousměrné není zaručeno, že k sekvencování nebo duplicitám. Datagramy také nemusí být spolehlivé; Neúspěšné dorazí. Data datagramu může do mimo pořadí a může být duplicitní, ale hranic záznamů v datech se zachovají, jako jsou menší než maximální velikost vnitřní příjemce záznamy. Jste odpovědní za správu o sekvencování a spolehlivost. (Spolehlivost spíše dobře na místní sítě [LAN], ale méně atd. celou oblast sítí WAN], jako je Internet).

Datagramy jsou "bez připojení", to znamená, že je vytvořeno žádné explicitní spojení; Odešlete zprávu datagram zadané soketu a může přijímat zprávy ze zadaného soketu.

Příklad datagram soketu je aplikace, která udržuje v síti synchronizované systémovými hodinami. To ukazuje další schopností sokety datagramu v alespoň nějaká nastavení: všesměrové vysílání zpráv do velkého počtu síťových adres.

Sokety datagramu jsou lepší než sokety datového proudu pro data orientovaná na záznamy. Další informace o sokety datagramu najdete v tématu Specifikace rozhraní Windows Sockets k dispozici v sadě Windows SDK.

## <a name="see-also"></a>Viz také:

[Windows Sockets v prostředí MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[Windows Sockets: Podrobnosti](../mfc/windows-sockets-background.md)

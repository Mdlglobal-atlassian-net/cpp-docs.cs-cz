---
title: 'Windows Sockets: Sokety datagramů | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sockets [MFC], datagram
- Windows Sockets [MFC], bi-directional data flow
- datagram sockets [MFC]
- Windows Sockets [MFC], datagram
- sockets [MFC], bi-directional data flow
ms.assetid: bec16a1c-74c0-4ff9-8c18-c2d87897d264
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 30ad7cab43301ae2cb7ebcb1fb4dfa850090955d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33383939"
---
# <a name="windows-sockets-datagram-sockets"></a>Windows Sockets: Sokety datagramů
Tento článek popisuje sokety datagramu, jeden ze dvou typů soketu Windows, která je k dispozici. (Další typ je [datového proudu soketu](../mfc/windows-sockets-stream-sockets.md).)  
  
 Sokety datagramu podporovat toku dat obousměrného, který není zaručena sekvencování nebo unduplicated. Datagramy také nemusí být spolehlivé; příchod volání můžou selhat. Datagram dat může dorazí mimo pořadí a může být duplicitní, ale záznamů hranice v datech se zachovají, tak dlouho, dokud záznamy jsou menší než omezení velikosti interní příjemce. Jste zodpovědní za správu sekvencování a spolehlivosti. (Spolehlivost obvykle nebyla narušena na místní sítě [LAN], ale méně tak dále WAN sítě [WAN], jako je Internet.)  
  
 Datagramy jsou "bez připojení", který je žádné explicitní připojení; Odeslat zprávu datagram na zadaný soket a může přijímat zprávy ze zadané soketu.  
  
 Příkladem datagram soketu je aplikace, která udržuje v síti, které jsou synchronizovány systémové hodiny. To ukazuje další schopností sokety datagramů v alespoň některá nastavení: vysílání zpráv velký počet síťových adres.  
  
 Sokety datagramu jsou lepší, než sokety datového proudu pro data orientovaná na záznamy. Další informace o sokety datagramu najdete v rozhraní Windows Sockets specifikaci, k dispozici v sadě Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Windows Sockets v prostředí MFC](../mfc/windows-sockets-in-mfc.md)   
 [Windows Sockets: Pozadí](../mfc/windows-sockets-background.md)


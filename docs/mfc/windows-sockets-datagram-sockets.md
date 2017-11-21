---
title: "Windows Sockets: Sokety datagramů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- sockets [MFC], datagram
- Windows Sockets [MFC], bi-directional data flow
- datagram sockets [MFC]
- Windows Sockets [MFC], datagram
- sockets [MFC], bi-directional data flow
ms.assetid: bec16a1c-74c0-4ff9-8c18-c2d87897d264
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d004bae6e4a15ab9c2aa76da76eb450c92572199
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="windows-sockets-datagram-sockets"></a>Windows Sockets: Sokety datagramů
Tento článek popisuje sokety datagramu, jeden ze dvou typů soketu Windows, která je k dispozici. (Další typ je [datového proudu soketu](../mfc/windows-sockets-stream-sockets.md).)  
  
 Sokety datagramu podporovat toku dat obousměrného, který není zaručena sekvencování nebo unduplicated. Datagramy také nemusí být spolehlivé; příchod volání můžou selhat. Datagram dat může dorazí mimo pořadí a může být duplicitní, ale záznamů hranice v datech se zachovají, tak dlouho, dokud záznamy jsou menší než omezení velikosti interní příjemce. Jste zodpovědní za správu sekvencování a spolehlivosti. (Spolehlivost obvykle nebyla narušena na místní sítě [LAN], ale méně tak dále WAN sítě [WAN], jako je Internet.)  
  
 Datagramy jsou "bez připojení", který je žádné explicitní připojení; Odeslat zprávu datagram na zadaný soket a může přijímat zprávy ze zadané soketu.  
  
 Příkladem datagram soketu je aplikace, která udržuje v síti, které jsou synchronizovány systémové hodiny. To ukazuje další schopností sokety datagramů v alespoň některá nastavení: vysílání zpráv velký počet síťových adres.  
  
 Sokety datagramu jsou lepší, než sokety datového proudu pro data orientovaná na záznamy. Další informace o sokety datagramu najdete v rozhraní Windows Sockets specifikaci, k dispozici v sadě Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Windows Sockets v prostředí MFC](../mfc/windows-sockets-in-mfc.md)   
 [Windows Sockets: pozadí](../mfc/windows-sockets-background.md)


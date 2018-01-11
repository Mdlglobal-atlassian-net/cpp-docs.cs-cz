---
title: 'Windows Sockets: Stream Sockets | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Windows Sockets [MFC], stream sockets
- sockets [MFC], stream sockets
- stream sockets [MFC]
ms.assetid: 31faaa34-a995-493f-a30b-b8115293d619
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bc112bd3cfbf1194a2898afecb513edcbc456747
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="windows-sockets-stream-sockets"></a>Windows Sockets: Sokety datového proudu
Tento článek popisuje sokety datového proudu, jeden ze dvou typů soketu Windows, která je k dispozici. (Další typ je [datagram soketu](../mfc/windows-sockets-datagram-sockets.md).)  
  
 Sokety datového proudu přinášejí tok dat bez záznamů hranice: datového proudu bajtů, které mohou být obousměrné (aplikace je plně duplexní: může současně přenášet a přijímat prostřednictvím soket). Datové proudy můžete spoléhat k poskytování sekvencované, unduplicated data. ("Sekvencování" znamená, že pakety jsou dodávány v pořadí, odeslány. "Unduplicated" znamená získat konkrétní paket pouze jednou.) Záruku, že přijetí datového proudu zpráv a datových proudů se skvěle hodí pro zpracování velkých objemů dat.  
  
 Síťová transportní vrstva může rozdělit nebo seskupení dat do paketů přiměřené velikosti. `CSocket` Třída bude zpracovávat balení a rozbalování za vás.  
  
 Datové proudy, které jsou založené na explicitní připojení: soketu A žádosti o připojení k soketu B; Socket B přijme nebo odmítne požadavek na připojení.  
  
 Telefonního hovoru poskytuje dobrou analogií pro datový proud. Za normálních podmínek přijímající strany slyší sdělení ve sdělení, bez duplikace nebo ke ztrátě pořadí. Sokety datového proudu jsou vhodné například pro implementace například protokolu FTP (File Transfer), což usnadňuje přenášení ASCII nebo binární soubory libovolné velikosti.  
  
 Pokud data musí být zaručené doručení a pokud je velká velikost dat, je vhodnější sokety datagramů sokety datového proudu. Další informace o sokety datového proudu najdete v rozhraní Windows Sockets specifikaci. Specifikace je k dispozici v sadě Windows SDK.  
  
 Sokety datového proudu pomocí může být vyšší než aplikace, které jsou navržené tak, aby použití soketu datagram pro všesměrové vysílání pro všechna přijímací sockets v síti, protože  
  
-   Model všesměrového vysílání podléhá problémy se sítí záplavy (nebo "storm").  
  
-   Model klient server přijata později je efektivnější.  
  
-   Model datového proudu poskytuje přenos dat spolehlivé, kde datagram modelu neexistuje.  
  
-   Poslední model využívá výhod umožňuje komunikaci mezi kódování Unicode a ANSI soketu aplikace třídy, které CArchive slouží pro třídu CSocket.  
  
    > [!NOTE]
    >  Při použití třídy `CSocket`, je nutné použít datový proud. Kontrolní výrazy MFC selže, pokud je zadat typ soketu jako **SOCK_DGRAM**.  
  
## <a name="see-also"></a>Viz také  
 [Windows Sockets v prostředí MFC](../mfc/windows-sockets-in-mfc.md)   
 [Windows Sockets: Pozadí](../mfc/windows-sockets-background.md)


---
title: 'Rozhraní Windows Sockets: Stream sokety | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows Sockets [MFC], stream sockets
- sockets [MFC], stream sockets
- stream sockets [MFC]
ms.assetid: 31faaa34-a995-493f-a30b-b8115293d619
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 87045d02238071170d776ff1675fb7283d1295bd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423855"
---
# <a name="windows-sockets-stream-sockets"></a>Windows Sockets: Sokety datového proudu

Tento článek popisuje sokety datového proudu, jeden ze dvou typů Windows Socket, která je k dispozici. (Je typ [datagram soketu](../mfc/windows-sockets-datagram-sockets.md).)

Sokety Stream zadejte pro tok dat bez hranic záznamů: datového proudu bajtů, které mohou být obousměrné (aplikace je plně duplexní: může současně přenášet a přijímat přes soket). Datové proudy lze dovolávat pro doručení sekvencované, zamezení duplicitám data. ("Správným seřazením" se rozumí, že pakety budou doručeny v pořadí odeslání. "Zamezení duplicitám" znamená získání konkrétního paketu pouze jednou.) Je zaručeno přijetí datového proudu zpráv a datových proudů se skvěle hodí pro zpracování velkých objemů dat.

Síťová transportní vrstva může rozdělit nebo data seskupit do paketů rozumnou velikost. `CSocket` Třídy bude zpracovávat komprimaci a rozbalování za vás.

Datové proudy jsou založeny na explicitní připojení: soketu A žádosti o připojení k soketu B; soket B přijme nebo odmítne žádost o připojení.

Telefonní hovor poskytuje dobré přirovnání pro datový proud. Za normálních okolností přijímající straně slyší, třeba v pořadí, že to říkáte, bez duplikace nebo ztráty. Stream sockets jsou vhodné například pro implementace například protokol FTP (File Transfer), což usnadňuje přenášení ASCII nebo binární soubory libovolné velikosti.

Stream sockets jsou upřednostňovány vůči sokety datagramu, kdy data musí být zaručené doručení a velikost dat je velká. Další informace o sokety datového proudu naleznete v tématu Specifikace rozhraní Windows Sockets. Specifikace je k dispozici v sadě Windows SDK.

Použití sokety datového proudu, může být vyšší než aplikace navržena pro použití soketů datagramu pro všesměrové vysílání pro všechna přijímací sockets v síti, protože

- Vysílání model je v souladu s problémy se sítí zahlcení (nebo "storm").

- Model klient server přijata později je mnohem efektivnější.

- Model služby stream poskytuje spolehlivý datový přenos, kde datagram model nemá.

- Finálního modelu využívá umožňuje komunikaci mezi kódování Unicode a ANSI soketu aplikace třídy, které CArchive slouží k csocket – třída.

    > [!NOTE]
    >  Pokud použijete třídu `CSocket`, je nutné použít datový proud. MFC kontrolní výraz selže, pokud zadáte typ soketu jako **SOCK_DGRAM**.

## <a name="see-also"></a>Viz také

[Windows Sockets v prostředí MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[Windows Sockets: Pozadí](../mfc/windows-sockets-background.md)


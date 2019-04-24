---
title: 'Windows Sockets: Stream Sockets'
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], stream sockets
- sockets [MFC], stream sockets
- stream sockets [MFC]
ms.assetid: 31faaa34-a995-493f-a30b-b8115293d619
ms.openlocfilehash: 91f06c4a36e76638708edf085987e51418913fd6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62337827"
---
# <a name="windows-sockets-stream-sockets"></a>Windows Sockets: Stream Sockets

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

## <a name="see-also"></a>Viz také:

[Windows Sockets v prostředí MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[Windows Sockets: Background](../mfc/windows-sockets-background.md)

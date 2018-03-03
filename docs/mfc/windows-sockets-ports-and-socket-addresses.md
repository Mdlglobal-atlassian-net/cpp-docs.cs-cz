---
title: "Windows Sockets: Porty a adresy soketů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- ports [MFC], definition
- Windows Sockets [MFC], ports
- Windows Sockets [MFC], addresses
- ports [MFC]
- addresses [MFC], socket
- sockets [MFC], addresses
- sockets [MFC], ports
ms.assetid: e050261a-9285-4f31-a1c5-6c8033af5b4a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0c7b2e15761815b75ba8001ad4eb5a5c276f5056
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="windows-sockets-ports-and-socket-addresses"></a>Windows Sockets: Porty a adresy soketů
Tento článek vysvětluje podmínky "port" a "address" jako použít s Windows Sockets.  
  
##  <a name="_core_port"></a>Port  
 Port identifikuje jedinečný proces, pro které je nutné zadat služby. V rámci tohoto portu je přidružené aplikace, která podporuje rozhraní Windows Sockets. Na nápad je jednoznačně identifikovat každou aplikaci Windows Sockets tak může mít více než jeden Windows Sockets aplikaci spuštěnou na počítači ve stejnou dobu.  
  
 Některé porty jsou vyhrazené pro běžné služby jako FTP. Neměli byste pomocí těchto portů, pokud zadáte tento druh služby. Specifikace rozhraní Windows Sockets podrobné informace o těchto rezervovaným portům. Soubor rozhraní WINSOCK. H také uvádí je.  
  
 Umožníte Knihovnu Windows Sockets vyberte použitelné port můžete předáte jako hodnota portu 0. MFC vybírá větší než 1 024 jednotek desetinnou hodnotu portu. Hodnota portu, který MFC vybrali voláním můžete načíst [CAsyncSocket::GetSockName](../mfc/reference/casyncsocket-class.md#getsockname) – členská funkce.  
  
##  <a name="_core_socket_address"></a>Adresy soketů  
 Každý objekt soketu souvisí s adresou Internet Protocol (IP) v síti. Adresa je obvykle název počítače, jako je například "ftp.microsoft.com", nebo desítkovém číslo, například "128.56.22.8".  
  
 Při hledání vytvořit soket obvykle není potřeba zadejte vlastní adresu.  
  
> [!NOTE]
>  Je možné, že váš počítač má několik síťových karet (nebo vaše aplikace může spustit jednou budete na takové počítači), každý představuje jinou síť. Pokud ano, budete muset uvést adresu k určení, které síťové karty, bude používat soketu. Toto je některé pokročilé využití a možné přenositelnost problém.  
  
 Další informace naleznete v tématu:  
  
-   [Windows Sockets – Použití třídy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets: Použití soketů s archivy](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows Sockets: Jak pracují sokety s archivy](../mfc/windows-sockets-how-sockets-with-archives-work.md)  
  
-   [Windows Sockets: Sokety streamu](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets: Sokety datagramů](../mfc/windows-sockets-datagram-sockets.md)  
  
## <a name="see-also"></a>Viz také  
 [Windows Sockets v prostředí MFC](../mfc/windows-sockets-in-mfc.md)


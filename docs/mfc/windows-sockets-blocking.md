---
title: "Windows Sockets: Blokování | Microsoft Docs"
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
- sockets [MFC], blocking mode
- Windows Sockets [MFC], Windows platforms
- Windows Sockets [MFC], blocking mode
- sockets [MFC], behavior on different Windows platforms
- blocking mode sockets
ms.assetid: 10aca9b1-bfba-41a8-9c55-ea8082181e63
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b4b54b78034037e9f3b015d7c1f67bb33771248c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="windows-sockets-blocking"></a>Windows Sockets: Blokování
V tomto článku a dvě doprovodné články vysvětlují několik problémů v rozhraní Windows Sockets programování. Tento článek se zabývá blokování. Další problémy, které jsou popsané v článcích: [Windows Sockets: pořadí bajtů](../mfc/windows-sockets-byte-ordering.md) a [Windows Sockets: převádění řetězců](../mfc/windows-sockets-converting-strings.md).  
  
 Pokud používáte nebo odvozena od třídy [CAsyncSocket](../mfc/reference/casyncsocket-class.md), budete muset řešení těchto problémů. Pokud používáte nebo odvozena od třídy [CSocket](../mfc/reference/csocket-class.md), spravuje MFC za vás.  
  
## <a name="blocking"></a>Blokování  
 Soket může být v "režimu blokování" nebo "neblokový režimu." Funkce soketů v režimu blokování (nebo synchronní) nevrátí, dokud se jejich akci dokončit. Tento postup se nazývá blokování protože soketu, jejichž funkce byla zavolána nemůžete udělat nic – blokováno – dokud vrátí volání. Volání **Receive** – členská funkce, například může trvat dokončit, protože se čeká na odesílající aplikací k odeslání nahodile dlouho (to je, pokud používáte `CSocket`, nebo pomocí `CAsyncSocket` s blokování). Pokud `CAsyncSocket` objekt je v neblokový režimu (operační asynchronně), vrátí volání okamžitě a aktuální kód chyby, se dá načíst [GetLastError](../mfc/reference/casyncsocket-class.md#getlasterror) – členská funkce je **WSAEWOULDBLOCK**, která určuje, že by blokovaly volání, kdyby se nebyla vrácena okamžitě z důvodu režimu. (`CSocket` nikdy vrátí **WSAEWOULDBLOCK**. Třída spravuje blokování za vás.)  
  
 Chování sockets se liší v 32bitové a 64bitové verze operačních systémů (například systému Windows 95 nebo Windows 98) než v části 16bitové operačních systémů (například systému Windows 3.1). Na rozdíl od 16bitové operační systémy 32bitové a 64bitové verze operačních systémů použít preemptivní multitasking a zadejte více vláken. V části 32bitové a 64bitové verze operačních systémů můžou vaše sockets v samostatných pracovních vláken. Soket ve vlákně můžete blokovat bez zasahování další aktivity v aplikaci a bez výdaje dobu výpočtů na blokování. Informace o vícevláknové programování, najdete v článku [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).  
  
> [!NOTE]
>  Vícevláknové aplikace, můžete v blokování povaha `CSocket` zjednodušit návrh vašeho programu bez ovlivnění odezvy uživatelského rozhraní. Pomocí zpracování interakcí v hlavní vlákno a `CSocket` zpracování v alternativní vláken, můžete oddělit tyto logické operace. V aplikaci, která není s více vlákny, musí být tyto dvě aktivity kombinaci a spravovány jako jedním vláknem, a to obvykle znamená použití `CAsyncSocket` tak může zpracovávat požadavky na komunikaci na vyžádání nebo přepsání `CSocket::OnMessagePending` pro zpracování akcí uživatele během zdlouhavé synchronní aktivity.  
  
 Zbytek Tato diskuse se pro programátory v jazyce cílení 16bitové operační systémy:  
  
 Za normálních okolností Pokud používáte `CAsyncSocket`, měli byste nepoužívejte blokování operace a pracovat asynchronně místo. V asynchronních operací z bodu příjmu **WSAEWOULDBLOCK** kód chyby po volání **Receive**, například čekat vaší `OnReceive` – členská funkce je volána oznámení můžete, který si můžete přečíst znovu. Asynchronní volání jsou provedené zpětné volání funkce oznámení vaše soketu odpovídající zpětného volání, jako například [události OnReceive](../mfc/reference/casyncsocket-class.md#onreceive).  
  
 V části Windows blokování volání jsou považovány za chybný postup. Ve výchozím nastavení [CAsyncSocket](../mfc/reference/casyncsocket-class.md) podporuje asynchronní volání a musí spravovat blokování sami pomocí zpětné volání oznámení. Třída [CSocket](../mfc/reference/csocket-class.md), na druhé straně je synchronní. To čerpadla zpráv systému Windows a spravuje blokování za vás.  
  
 Další informace o blokování najdete v rozhraní Windows Sockets specifikaci. Další informace o "Na" funkce najdete v tématu [Windows Sockets: oznámení soketů](../mfc/windows-sockets-socket-notifications.md) a [Windows Sockets: odvozování z tříd soketů](../mfc/windows-sockets-deriving-from-socket-classes.md).  
  
 Další informace naleznete v tématu:  
  
-   [Windows Sockets – Použití třídy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets: Použití soketů s archivy](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows Sockets: Pozadí](../mfc/windows-sockets-background.md)  
  
-   [Windows Sockets: Sokety streamu](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets: Sokety datagramů](../mfc/windows-sockets-datagram-sockets.md)  
  
## <a name="see-also"></a>Viz také  
 [Windows Sockets v prostředí MFC](../mfc/windows-sockets-in-mfc.md)   
 [CAsyncSocket::OnSend](../mfc/reference/casyncsocket-class.md#onsend)


---
title: "Windows Sockets: Soketu oznámení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Windows Sockets [MFC], notifications
- notifications [MFC], socket
- sockets [MFC], notifications
ms.assetid: 87d5bf70-6e77-49a9-9a64-aaadee2ad018
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d37a45443efe1ad45e21c5729907135d0e037baa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="windows-sockets-socket-notifications"></a>Windows Sockets: Oznámení soketů
Tento článek popisuje funkce oznámení v tříd soketů. Tyto členské funkce jsou funkce zpětného volání, které volá framework oznámit vaše objekt soketu se o důležitých událostech. Funkce oznámení jsou:  
  
-   [Události OnReceive](../mfc/reference/casyncsocket-class.md#onreceive): upozorní tento soketu se data ve vyrovnávací paměti pro něj k načtení voláním [Receive](../mfc/reference/casyncsocket-class.md#receive).  
  
-   [OnSend](../mfc/reference/casyncsocket-class.md#onsend): upozorní tento soketu, teď může posílat data voláním [odeslat](../mfc/reference/casyncsocket-class.md#send).  
  
-   [OnAccept](../mfc/reference/casyncsocket-class.md#onaccept): upozorní tento naslouchání soketu, který může přijmout čekající žádosti o připojení voláním [přijmout](../mfc/reference/casyncsocket-class.md#accept).  
  
-   [OnConnect](../mfc/reference/casyncsocket-class.md#onconnect): upozorní tento připojování soketu dokončení jeho pokus o připojení: pravděpodobně úspěšně nebo možná v chybě.  
  
-   [Onclose –](../mfc/reference/casyncsocket-class.md#onclose): upozorní tento soketu, který je připojený k soketu zavřel.  
  
    > [!NOTE]
    >  Funkce další oznámení je [OnOutOfBandData](../mfc/reference/casyncsocket-class.md#onoutofbanddata). Toto oznámení informuje přijímající soketu, že odesílání soketu má "out-of-band" data k odeslání. Out-of-band data jsou logicky nezávislý na kanál spojené s každou dvojici sokety datového proudu připojené. Kanál out-of-band se obvykle používá k odesílání dat "naléhavé". MFC podporuje out-of-band data. Rozšířené uživatelů, kteří pracují s třídou [CAsyncSocket](../mfc/reference/casyncsocket-class.md) může být nutné použít out-of-band kanál, ale uživatelé třídy [CSocket](../mfc/reference/csocket-class.md) se nedoporučuje v jeho použití. Jednodušší způsob je vytvořit druhý soket pro předávání taková data. Další informace o datech out-of-band najdete v rozhraní Windows Sockets specifikaci, k dispozici v sadě Windows SDK.  
  
 Pokud odvozujete od třídy `CAsyncSocket`, je nutné přepsat funkce oznámení pro ty síťové události týkající se do vaší aplikace. Pokud odvodíte třídu od třídy `CSocket`, je věcí vaší volby zda mají být přepsány funkce oznámení, které vás zajímají. Můžete také použít `CSocket` samostatně, v takovém případě oznámení funkce výchozí k žádným způsobem.  
  
 Tyto funkce jsou funkce přepisovatelné zpětného volání. `CAsyncSocket`a `CSocket` převést zprávy pro oznámení, ale musí implementovat, jak oznámení funkce reakce, pokud chcete používat. Funkce oznámení se označují jako v době, kdy je vaše soketu upozornění na událost, které vás zajímají, jako je například přítomnosti dat čtení.  
  
 MFC volá funkce oznámení k umožňují přizpůsobit chování vaší soketu v době, kdy je upozornění. Například může volat **Receive** z vaší `OnReceive` funkce oznámení, tedy na vrácení oznámení data ke čtení, zavoláte **Receive** k jeho čtení. Tento přístup není nutné, ale je platný scénář. Jako alternativu, můžete použít funkce oznámení sledovat průběh, vytisknout **trasování** zprávy a tak dále.  
  
 Přepisování funkcí oznámení v třídě odvozené soketu a poskytnutím implementace můžete využít výhod těchto oznámení.  
  
 Během operace jako je příjem a odesílání dat `CSocket` objektu se změní na synchronní. V průběhu synchronního stavu jsou žádné oznámení určené výhradně pro jiné sockets do fronty při aktuální soketu čeká na oznámení, která požaduje. (Například během **Receive** volání, která chce soket oznámení ke čtení.) Jakmile soket skončí její synchronní operace a stane asynchronní znovu, můžete začít jiných sockets příjem oznámení ve frontě.  
  
> [!NOTE]
>  V `CSocket`, `OnConnect` volána funkce oznámení. Pro připojení, volejte **Connect**, který se vrátí po dokončení připojení (úspěšně nebo chyba). Zpracování oznámení připojení je podrobností implementace MFC.  
  
 Podrobnosti o každé funkci oznámení najdete v tématu funkce pod třídou `CAsyncSocket` v *odkaz knihovny MFC*. Zdrojový kód a informace o MFC ukázky najdete v tématu [MFC ukázky](../visual-cpp-samples.md).  
  
 Další informace naleznete v tématu:  
  
-   [Windows Sockets: Použití třídy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets: Odvozování z tříd soketů](../mfc/windows-sockets-deriving-from-socket-classes.md)  
  
-   [Windows Sockets: Jak pracují sokety s archivy](../mfc/windows-sockets-how-sockets-with-archives-work.md)  
  
-   [Windows Sockets: blokování](../mfc/windows-sockets-blocking.md)  
  
-   [Windows Sockets: Pořadí bajtů](../mfc/windows-sockets-byte-ordering.md)  
  
-   [Windows Sockets: Převádění řetězců](../mfc/windows-sockets-converting-strings.md)  
  
## <a name="see-also"></a>Viz také  
 [Windows Sockets v prostředí MFC](../mfc/windows-sockets-in-mfc.md)


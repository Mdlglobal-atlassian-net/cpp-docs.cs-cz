---
title: "OLE – pozadí: Kontejnery a servery | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE full-server applications [MFC]
- server applications [MFC], communication with containers
- full-server [MFC]
- server applications [MFC], requirements
- server applications [MFC], defined
- OLE server applications [MFC], about server applications
- server applications [MFC], full-server vs. mini-server
- OLE server applications [MFC], mini-server applications
- OLE containers [MFC], container applications
- containers [MFC], OLE container applications
- server applications [MFC]
ms.assetid: dafbb31d-096c-4654-b774-12900d832919
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b3c6f3c15b0ea398ec621ba5f6e34a9fb6e0aae8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ole-background-containers-and-servers"></a>OLE – pozadí: Kontejnery a servery
Aplikace kontejneru je aplikace, která může obsahovat vložené nebo propojené položky do svých vlastních dokumentů. Dokumenty spravuje aplikace kontejneru musí být schopný k uložení a zobrazení OLE dokumentu součásti a také data vytvořená pomocí vlastní aplikace. Aplikace kontejneru musí také umožňují uživatelům vložit nové položky nebo upravit existující položky tak, že aktivace serverové aplikace, pokud je to nezbytné. Požadavky uživatelského rozhraní aplikace kontejneru jsou uvedené v článku [kontejnery: problémy uživatelského rozhraní](../mfc/containers-user-interface-issues.md).  
  
 Serverová aplikace nebo součásti aplikace je aplikace, která můžete vytvořit OLE dokumentu komponenty pro použití aplikace typu kontejner. Aplikace serveru obvykle podporují přetahování nebo kopírování svá data do schránky, tak, aby aplikace kontejneru můžete vložit data jako vložené nebo propojené položky. Aplikace může být kontejner i server.  
  
 Většina serverů jsou samostatné aplikace nebo úplné serverů; jsou lze buď spustit jako samostatné aplikace nebo může být spuštěn aplikace kontejneru. Miniserver je zvláštním typem aplikace server, který může být spuštěn pouze kontejner. Není možné spustit jako samostatnou aplikaci. Servery Microsoft Draw a Microsoft Graph jsou příklady miniservers.  
  
 Kontejnery a servery nekomunikují přímo. Místo toho komunikují prostřednictvím OLE systému dynamické knihovny (DLL). Tyto knihovny poskytují funkce, které volají kontejnery a servery a kontejnery a servery poskytují funkce zpětného volání, které volají knihovny DLL.  
  
 Pomocí to znamená komunikace, kontejner není nutné znát podrobnosti implementace serverové aplikace. To umožňuje kontejner tak, aby přijímal položky vytvořené jakémukoli serveru, aniž by bylo nutné definovat typy serverů, se kterými můžete pracovat. Uživatel aplikace kontejneru v důsledku toho můžete využít výhod budoucí aplikace a datových formátů. Pokud jsou tyto nové aplikace OLE součásti, složeného dokumentu bude možné začlenit položky vytvořené pomocí těchto aplikací.  
  
## <a name="see-also"></a>Viz také  
 [OLE – pozadí](../mfc/ole-background.md)   
 [OLE – pozadí: Implementace MFC](../mfc/ole-background-mfc-implementation.md)   
 [Kontejnery](../mfc/containers.md)   
 [Servery](../mfc/servers.md)   
 [Kontejnery: Klientské položky](../mfc/containers-client-items.md)   
 [Servery: Serverové položky](../mfc/servers-server-items.md)


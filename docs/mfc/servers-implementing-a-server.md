---
title: 'Servery: Implementace serveru | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- servers, implementing
- OLE server applications [MFC], implementing OLE servers
ms.assetid: 5bd57e8e-3b23-4f23-9597-496fac2d24b5
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4ed4ca1b131e56b2735b3a6e4ba408f3ad79b8de
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="servers-implementing-a-server"></a>Servery: Implementace serveru
Tento článek vysvětluje kód, který vytvoří Průvodce aplikací MFC pro visual úpravy serverová aplikace. Pokud nepoužíváte aplikaci průvodce, tento článek obsahuje seznam oblastí, kde musíte napsat kód pro implementaci serverové aplikace.  
  
 Pokud používáte Průvodce aplikace k vytvoření nové serverové aplikace, nabízí významné množství kódu pro konkrétní server za vás. Pokud přidáváte visual úpravy funkce serveru do existující aplikace, musí se duplicitní kód, který by před přidáním zbytek kód nezbytné serveru zadali v Průvodce vytvořením aplikace.  
  
 Kód serveru, který poskytuje v Průvodce vytvořením aplikace, které patří do několika kategorií:  
  
-   Definování prostředky serveru:  
  
    -   V nabídce prostředku používaného pro server je úpravy vložené položky v samostatném okně.  
  
    -   Nabídek a panelů nástrojů prostředky využívané server je aktivní na místě.  
  
     Další informace o těchto prostředků najdete v tématu [nabídky a prostředky: serverové doplňky](../mfc/menus-and-resources-server-additions.md).  
  
-   Definování třídu položky odvozené z `COleServerItem`. Další informace o serveru položky v [servery: Server položky](../mfc/servers-server-items.md).  
  
-   Změna základní třídu třídy pro dokument `COleServerDoc`. Další podrobnosti najdete v tématu [servery: implementace dokumentů serveru](../mfc/servers-implementing-server-documents.md).  
  
-   Definování oken s rámečkem třídy odvozené od `COleIPFrameWnd`. Další podrobnosti najdete v tématu [servery: implementace oken s rámečkem na místě](../mfc/servers-implementing-in-place-frame-windows.md).  
  
-   Vytvoření položka pro příslušnou aplikaci na server v databázi registrace Windows a registrace novou instanci serveru se systémem OLE. Informace v tomto tématu najdete v tématu [registrace](../mfc/registration.md).  
  
-   Inicializace a spuštění aplikace serveru. Informace v tomto tématu najdete v tématu [registrace](../mfc/registration.md).  
  
 Další informace najdete v tématu [COleServerItem](../mfc/reference/coleserveritem-class.md), [COleServerDoc](../mfc/reference/coleserverdoc-class.md), a [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md) v *knihovny tříd*.  
  
## <a name="see-also"></a>Viz také  
 [Servery](../mfc/servers.md)   
 [Kontejnery](../mfc/containers.md)   
 [Nabídky a prostředky (OLE)](../mfc/menus-and-resources-ole.md)   
 [Registrace](../mfc/registration.md)


---
title: 'Servery: Implementace serveru | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- servers, implementing
- OLE server applications [MFC], implementing OLE servers
ms.assetid: 5bd57e8e-3b23-4f23-9597-496fac2d24b5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0ea51d6cd811572d73b0de64072f3d335e2682fd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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


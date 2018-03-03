---
title: "Aktivace: Příkazy | Microsoft Docs"
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
- verbs [MFC]
- OLE [MFC], activation
- edit verb [MFC]
- activation [MFC], verbs
- OLE [MFC], editing
- Primary verb [MFC]
- OLE activation {MFC]
ms.assetid: eb56ff23-1de8-43ad-abeb-dc7346ba7b70
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c2a443f4ce65dcc7e9460bd016638aa5069e7e6d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="activation-verbs"></a>Aktivace: Příkazy
Tento článek vysvětluje play příkazy primární a sekundární roli v prostředí OLE [aktivace](../mfc/activation-cpp.md).  
  
 Dvakrát klikněte na položku embedded obvykle umožňuje uživateli upravit. Některé položky však nefungují tak tímto způsobem. Například dvakrát klikněte na položku vytvořen záznam zvuku aplikací neotevře serveru v samostatném okně; Místo toho hraje zvuk.  
  
 Důvody, proč tento rozdíl chování je, že záznam zvuku položky mají různé "primární operaci." Primární požadavek je akce provést při poklepání položku OLE. Pro většinu typů OLE – položky je primární požadavek úpravy, který spouští server, který položku vytvořil. Pro některé typy položek, jako jsou položky záznam zvuku je primární požadavek Play.  
  
 Mnoho typů položek OLE podporují jenom jedna operace a upravit je nejběžnější. Některé typy položek však podporovat více příkazů. Můžete třeba upravit záznam zvuku položky podporují jako sekundární operaci.  
  
 Další akce často používaná je otevřené. Příkaz otevřete je stejný jako úpravy, s výjimkou je server aplikace spuštěna v samostatném okně. Tato operace se mají použít při kontejnerové aplikace nebo aplikaci server nepodporuje aktivace na místě.  
  
 Všechny příkazy než primární požadavek musí být volána prostřednictvím příkazu podnabídky, když je vybrána položka. Tento dílčí obsahuje všechny operace podporována položkou a je obvykle dosaženo pomocí *typename* **objekt** příkaz na **upravit** nabídky. Informace o *typename* **objekt** příkaz, naleznete v článku [nabídky a prostředky: kontejnerové doplňky](../mfc/menus-and-resources-container-additions.md).  
  
 Příkazy, které podporuje aplikace server jsou uvedeny v registrační databázi systému Windows. Pokud je serverová aplikace napsané pomocí knihovny Microsoft Foundation Class, se budou automaticky zaregistrovat všechny operace, při spuštění serveru. V opačném případě byste měli zaregistrovat během fáze inicializace serverová aplikace. Další informace najdete v článku [registrace](../mfc/registration.md).  
  
## <a name="see-also"></a>Viz také  
 [Aktivace](../mfc/activation-cpp.md)   
 [Kontejnery](../mfc/containers.md)   
 [Servery](../mfc/servers.md)


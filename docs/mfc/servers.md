---
title: Servery | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE server applications [MFC]
- OLE server applications [MFC], activation
- full-server
- servers
- mini-server
- OLE server applications [MFC], server types
- server applications [MFC]
ms.assetid: e45172e8-eae3-400a-8139-0fa009a42fdc
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: be83831c79b398de9e9b0791d172cf7608e322aa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="servers"></a>Servery
Aplikace serveru (nebo součásti aplikace) vytvoří aplikace typu kontejner OLE položky (nebo součásti) pro použití. Visual úpravy serverová aplikace také podporuje úpravy s náhledem nebo aktivace na místě. Jinou formu OLE serveru je [automatizační server](../mfc/automation-servers.md). Některé serverové aplikace podporují pouze vytváření vložené položky; ostatní podporují vytvoření vložené a propojené položky. I když toto je výjimečná některé podporují pouze propojení. Všechny aplikace server musí podporovat aktivace aplikace typu kontejner, pokud chce uživatel upravovat položky. Aplikace může být kontejner i server. Jinými slovy ho můžete obě začlenit dat do své dokumenty a vytvořit data, která lze vložit jako položky do dalších aplikací dokumenty.  
  
 Miniserver je zvláštním typem aplikace server, který může být spuštěn pouze kontejner. Microsoft Draw a Microsoft Graph jsou příklady miniservers. Miniserver nejsou uložené dokumenty jako soubory na disku. Místo toho přečte jeho dokumenty z a zapisuje je do položek v dokumentech patřící do kontejnerů. V důsledku toho miniserver podporuje pouze vložení není propojení.  
  
 Celého serveru můžete spustit buď jako samostatné aplikace nebo spuštění aplikací kontejneru. Úplný server může ukládat dokumenty jako soubory na disku. Může podporovat pouze vložení obou vložení a propojení nebo pouze propojení. Uživatel aplikace kontejner může vytvořit položku embedded tak, že zvolíte příkazy vyjmutí a kopírování v serveru a příkaz Vložit v kontejneru. Propojené položky se vytvoří tak, že zvolíte příkaz Kopírovat na serveru a příkaz Vložit propojení v kontejneru. Uživatele můžete také vytvořit položku vložené nebo propojené pomocí dialogového okna Vložit objekt.  
  
 Následující tabulka shrnuje charakteristiky různé typy serverů:  
  
### <a name="server-characteristics"></a>Vlastnosti serveru  
  
|Typ serveru|Podporuje víc instancí|Počet položek na dokumentu|Dokumenty na instanci|  
|--------------------|---------------------------------|------------------------|----------------------------|  
|Miniserver|Ano|1|1|  
|Celého serveru SDI|Ano|1 (Pokud propojení je podporováno, 1 nebo více)|1|  
|Úplný server MDI|Ne (není požadováno)|1 (Pokud propojení je podporováno, 1 nebo více)|0 nebo více|  
  
 Serverová aplikace by měly podporovat více kontejnerů současně, v případě, že více než jednoho kontejneru se použije k úpravě vložené nebo propojené položky. Pokud je server aplikace SDI (nebo miniserver s rozhraním dialogové okno pole), musí být možné současně spustit více instancí serveru. To umožňuje samostatnou instanci aplikace pro každý kontejner požadavek zpracovat.  
  
 Pokud je server aplikace MDI, může vytvořit nové podřízeného okna MDI pokaždé, když do kontejneru je potřeba upravit položku. Tímto způsobem může podporovat jednu instanci aplikace několika kontejnerů.  
  
 Aplikace serveru musí říct OLE systémové knihovny DLL, co dělat, pokud jedna instance serveru je již spuštěn, když se jiný kontejner požadavky jeho služby: zda by měla spustit novou instanci serveru nebo směrovat své žádosti všechny kontejnery na jednu instanci Server.  
  
 Další podrobnosti na serverech najdete v tématu:  
  
-   [Servery: Implementace serveru](../mfc/servers-implementing-a-server.md)  
  
-   [Servery: Implementace dokumentů serveru](../mfc/servers-implementing-server-documents.md)  
  
-   [Servery: Implementace oken s rámečkem na místě](../mfc/servers-implementing-in-place-frame-windows.md)  
  
-   [Servery: Serverové položky](../mfc/servers-server-items.md)  
  
-   [Servery: Problémy uživatelského rozhraní](../mfc/servers-user-interface-issues.md)  
  
## <a name="see-also"></a>Viz také  
 [OLE](../mfc/ole-in-mfc.md)   
 [Kontejnery](../mfc/containers.md)   
 [Kontejnery: Pokročilé funkce](../mfc/containers-advanced-features.md)   
 [Nabídky a prostředky (OLE)](../mfc/menus-and-resources-ole.md)   
 [Registrace](../mfc/registration.md)   
 [Automatizační servery](../mfc/automation-servers.md)


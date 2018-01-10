---
title: "Kontejnery: Stavy klientských položek | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE containers [MFC], client-item states
- states, OLE container client-item
- lifetime, lifetime states and OLE container client items
- client items and OLE containers
ms.assetid: e7021caa-bd07-4adb-976e-f5f3d025bc53
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6bcc43d4e8b32a8766eef7c50e45bece569ef5c3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="containers-client-item-states"></a>Kontejnery: Stavy klientských položek
Tento článek vysvětluje různé stavy, které klientské položky projdou v celé jeho životnosti.  
  
 Klientské položky projdou několik stavy, jako je vytvořen, aktivovat, upravit a uložit. Každý čas položky změny stavu, volání framework [COleClientItem::OnChange](../mfc/reference/coleclientitem-class.md#onchange) s `OLE_CHANGED_STATE` oznámení. Druhý parametr je hodnota z **COleClientItem::ItemState** výčtu. Může být jeden z následujících akcí:  
  
-   **COleClientItem::emptyState**  
  
-   **COleClientItem::loadedState**  
  
-   **COleClientItem::openState**  
  
-   **COleClientItem::activeState**  
  
-   **COleClientItem::activeUIState**  
  
 V prázdné stavu, klient položka ještě není úplně položku. Pro něj byl přidělen paměti, ale ještě nebyla inicializovaná daty položky OLE. Toto je stav položku klienta je v vytvořenou pomocí volání **nové** , ale ještě neprošel druhý krok vytvoření typické dvoustupňové.  
  
 V druhém kroku, provádět prostřednictvím volání `COleClientItem::CreateFromFile` nebo jiný **CreateFrom***xxxx* funkce, položka je zcela vytvořen. Byla přidružena data OLE (ze souboru nebo z jiného zdroje, jako např. schránku) `COleClientItem`-odvozené objektu. Položka se nyní v načíst stav.  
  
 Pokud položku má byl otevřen v okně serveru spíše než v místě v kontejneru dokument otevřít, je ve stavu otevřít (nebo plně otevřít). V tomto stavu je cross šrafování obvykle vykresluje přes reprezentaci položky v okně kontejneru indikující, že je položka jinde aktivní.  
  
 Když položka byla aktivována na místě, se předá, obvykle pouze stručně řečeno, prostřednictvím aktivním stavu. Potom vstupuje do stavu active uživatelského rozhraní, ve kterém se sloučil serveru jeho nabídky, panely nástrojů a další součásti uživatelského rozhraní s těmi, která kontejneru. Přítomnost tyto součásti uživatelského rozhraní rozlišuje aktivním stavu uživatelského rozhraní z aktivním stavu. Aktivním stavu, jinak se podobá aktivním stavu uživatelského rozhraní. Pokud je server podporuje vrácení zpět, je potřeba uchovávat informace zpět stav položky OLE, dokud nebude dosaženo stavu načíst nebo otevřete serveru.  
  
## <a name="see-also"></a>Viz také  
 [Kontejnery](../mfc/containers.md)   
 [Aktivace](../mfc/activation-cpp.md)   
 [Kontejnery: Oznámení klientských položek](../mfc/containers-client-item-notifications.md)   
 [Snímače](../mfc/trackers.md)   
 [CRectTracker – třída](../mfc/reference/crecttracker-class.md)

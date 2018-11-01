---
title: 'Kontejnery: Stavy klientských položek'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE containers [MFC], client-item states
- states, OLE container client-item
- lifetime, lifetime states and OLE container client items
- client items and OLE containers
ms.assetid: e7021caa-bd07-4adb-976e-f5f3d025bc53
ms.openlocfilehash: 866aa6f2265abe671ce0028e3be5f1c8ee1762a8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575341"
---
# <a name="containers-client-item-states"></a>Kontejnery: Stavy klientských položek

Tento článek popisuje různé stavy, které prochází položku klienta v průběhu své životnosti.

Klientské položky prochází několika stavů je vytvořen, aktivovat, upravit a uložit. Pokaždé, když změny stavu položky, rámec volá [COleClientItem::OnChange](../mfc/reference/coleclientitem-class.md#onchange) s **OLE_CHANGED_STATE** oznámení. Druhý parametr je hodnota z `COleClientItem::ItemState` výčtu. Může být jeden z následujících akcí:

- *COleClientItem::emptyState*

- *COleClientItem::loadedState*

- *COleClientItem::openState*

- *COleClientItem::activeState*

- *COleClientItem::activeUIState*

V prázdné stavu klientskou položku ještě není úplně položky. Pro něj byla přidělena paměť, ale dosud nebyla inicializována s daty položky OLE. Toto je stav položky klienta je v po vytvoření přímo pomocí volání **nové** , ale ještě neprošlo druhý krok typické dvoustupňové vytváření.

V druhém kroku provádí prostřednictvím volání `COleClientItem::CreateFromFile` nebo jiném `CreateFrom` *xxxx* funkce, tato položka je zcela vytvořena. Je přidružená data OLE (ze souboru nebo jiného zdroje, jako např. schránku) `COleClientItem`-odvozenému objektu. Položka je nyní v načíst stav.

Pokud položka má byl otevřen v okně serveru spíše než otevřít místo v dokumentu kontejneru, je ve stavu open (nebo zcela otevřená). V tomto stavu je mezi šrafování obvykle nakreslen přes reprezentace položky v okně kontejneru k označení, že položka je aktivní jinde.

Když se položka byla aktivována na místě, předá, obvykle pouze stručně, prostřednictvím aktivním stavu. Potom zadá aktivním stavu uživatelského rozhraní sloučil serveru své nabídky, panely nástrojů a další komponenty uživatelského rozhraní s těmi kontejneru. Přítomnost tyto součásti uživatelského rozhraní odlišuje aktivním stavu uživatelského rozhraní v aktivním stavu. V opačném případě se podobá aktivní stav aktivního stavu uživatelského rozhraní. Pokud server podporuje vrácení zpět, je potřeba uchovávat informace zpět stav položky OLE. dokud nebude dosaženo stavu nenačetl nebo je otevřít na serveru.

## <a name="see-also"></a>Viz také

[Kontejnery](../mfc/containers.md)<br/>
[Aktivace](../mfc/activation-cpp.md)<br/>
[Kontejnery: Oznámení klientských položek](../mfc/containers-client-item-notifications.md)<br/>
[Snímače](../mfc/trackers.md)<br/>
[CRectTracker – třída](../mfc/reference/crecttracker-class.md)

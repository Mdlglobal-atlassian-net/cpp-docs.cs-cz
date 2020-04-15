---
title: 'Servery: Serverové položky'
ms.date: 11/04/2016
helpviewer_keywords:
- server items, implementing
- servers [MFC], server items
- architecture [MFC], server-item
- server items
- OLE server applications [MFC], server items
ms.assetid: 28ba81a1-726a-4728-a52d-68bc7efd5a3c
ms.openlocfilehash: 8ae24104a30a0b44e92b889006907911124310f7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355116"
---
# <a name="servers-server-items"></a>Servery: Serverové položky

Když kontejner spustí server, aby uživatel mohl upravit vloženou nebo propojenou položku OLE, vytvoří serverová aplikace položku serveru. Položka serveru, která je objektem třídy `COleServerItem`odvozené z aplikace , poskytuje rozhraní mezi dokumentem serveru a aplikací kontejneru.

Třída `COleServerItem` definuje několik overridable členské funkce, které jsou volány OLE, obvykle v reakci na požadavky z kontejneru. Položky serveru mohou představovat část dokumentu serveru nebo celý dokument. Pokud je položka OLE vložena do dokumentu kontejneru, představuje položka serveru celý dokument serveru. Je-li položka OLE propojena, může položka serveru představovat část dokumentu serveru nebo celý dokument v závislosti na tom, zda je propojení s částí nebo s celkem.

V ukázce [HIERSVR](../overview/visual-cpp-samples.md) má například `CServerItem`třída položky serveru , člen, který `CServerNode`je ukazatelem na objekt třídy . Objekt `CServerNode` je uzel v dokumentu aplikace HIERSVR, což je strom. Pokud `CServerNode` je objekt kořenovým uzlem, `CServerItem` objekt představuje celý dokument. Pokud `CServerNode` je objekt podřízenýuzel, `CServerItem` objekt představuje část dokumentu. Příklad této interakce naleznete v příkladu ukázky [HIERSVR](../overview/visual-cpp-samples.md) knihovny MFC OLE.

## <a name="implementing-server-items"></a><a name="_core_implementing_server_items"></a>Implementace položek serveru

Pokud použijete průvodce aplikací k vytvoření "startér" kód pro vaši aplikaci, vše, co musíte udělat, aby zahrnutí položek serveru v počáteční kód je vybrat jednu z možností serveru ze stránky Možnosti OLE. Pokud přidáváte položky serveru do existující aplikace, proveďte následující kroky:

#### <a name="to-implement-a-server-item"></a>Implementace položky serveru

1. Odvodit `COleServerItem`třídu z .

1. V odvozené třídě přepište `OnDraw` členní funkci.

   Rozhraní framework `OnDraw` volá vykreslit položku OLE do metasouboru. Aplikace kontejneru používá tento metasoubor k vykreslení položky. Třída zobrazení aplikace má také `OnDraw` členní funkci, která se používá k vykreslení položky, když je serverová aplikace aktivní.

1. Implementujte přepsání třídy `OnGetEmbeddedItem` dokumentu serveru. Další informace naleznete v článku [Servery: Implementace dokumentů serveru](../mfc/servers-implementing-server-documents.md) a ukázka [HIERSVR](../overview/visual-cpp-samples.md)knihovny MFC OLE .

1. Implementujte člennou `OnGetExtent` funkci třídy položky serveru. Rozhraní Framework volá tuto funkci k načtení velikosti položky. Výchozí implementace neprovede žádné provádění.

## <a name="a-tip-for-server-item-architecture"></a><a name="_core_a_tip_for_server.2d.item_architecture"></a>Tip pro architekturu položky serveru

Jak je uvedeno v [části Implementace položek serveru](#_core_implementing_server_items), serverové aplikace musí být schopny vykreslit položky v zobrazení serveru i v metasouboru používaném aplikací kontejneru. V architektuře aplikace knihovny tříd microsoft foundation `OnDraw` členská funkce třídy zobrazení vykreslí položku při úpravách (viz [CView::OnDraw](../mfc/reference/cview-class.md#ondraw) v *odkazu na knihovnu tříd).* Položka serveru vykreslí `OnDraw` položku do metasouboru ve všech ostatních případech (viz [COleServerItem::OnDraw](../mfc/reference/coleserveritem-class.md#ondraw)).

Duplicitě kódu se můžete vyhnout tak, že napíšete pomocné funkce `OnDraw` ve třídě dokumentu serveru a zavoláte je z funkcí ve třídách zobrazení a položek serveru. MFC OLE ukázka [HIERSVR](../overview/visual-cpp-samples.md) používá `CServerView::OnDraw` tuto `CServerItem::OnDraw` strategii: funkce a obě volání `CServerDoc::DrawTree` k vykreslení položky.

Zobrazení a položka mají `OnDraw` členské funkce, protože jsou nakreslovány za různých podmínek. Zobrazení musí brát v úvahu takové faktory, jako je přiblížení, velikost a rozsah výběru, oříznutí a prvky uživatelského rozhraní, jako jsou posuvníky. Položka serveru, na druhé straně vždy kreslí celý objekt OLE.

Další informace naleznete v [tématech CView::OnDraw](../mfc/reference/cview-class.md#ondraw), [COleServerItem](../mfc/reference/coleserveritem-class.md), [COleServerItem::OnDraw](../mfc/reference/coleserveritem-class.md#ondraw)a [COleServerDoc::OnGetEmbeddedItem](../mfc/reference/coleserverdoc-class.md#ongetembeddeditem) v *odkazu knihovny tříd*.

## <a name="see-also"></a>Viz také

[Servery](../mfc/servers.md)

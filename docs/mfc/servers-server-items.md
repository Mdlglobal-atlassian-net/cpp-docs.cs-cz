---
title: 'Servery: Serverové položky | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- server items, implementing
- servers [MFC], server items
- architecture [MFC], server-item
- server items
- OLE server applications [MFC], server items
ms.assetid: 28ba81a1-726a-4728-a52d-68bc7efd5a3c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 72f8de75607921edda62aec9baec424066431d61
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438857"
---
# <a name="servers-server-items"></a>Servery: Serverové položky

Když kontejner spustí na serveru tak, aby uživatel může upravovat položky vložené nebo propojené OLE, server aplikace vytváří "položka serveru". Položka serveru, které je objekt třídy odvozené z `COleServerItem`, poskytuje rozhraní mezi dokumentu na serveru a aplikace typu kontejner.

`COleServerItem` Třída definuje několik přepisovatelné členské funkce, které jsou volány aplikací OLE, obvykle v reakci na žádosti z kontejneru. Položky na serveru může představovat část dokumentu na serveru nebo celý dokument. Položka serveru položky OLE se vloží do dokumentu kontejneru, představuje dokumentu celý server. Propojeného položky OLE. může představovat položku serveru část dokumentu na serveru nebo celý dokument v závislosti na tom, zda odkaz je část nebo celý.

V [HIERSVR](../visual-cpp-samples.md) vzorkovat, například třídy položka serveru `CServerItem`, má člen, který je ukazatel na objekt třídy `CServerNode`. `CServerNode` Objektu je uzel v dokumentu HIERSVR aplikace, což je strom. Když `CServerNode` objekt je kořenový uzel `CServerItem` objekt představuje celý dokument. Když `CServerNode` podřízený uzel, je objekt `CServerItem` objekt představuje součást dokumentu. Najdete v ukázce MFC OLE [HIERSVR](../visual-cpp-samples.md) příklad tuto interakci.

##  <a name="_core_implementing_server_items"></a> Implementace položky serveru

Pokud používáte Průvodce aplikací pro vytvoření "počáteční" kódu pro vaši aplikaci, jediné, co musíte udělat, aby zahrnout položky serveru počáteční kód je zvolte jednu z možností serveru ze stránky možností OLE. Pokud přidáváte server položky do existující aplikace, proveďte následující kroky:

#### <a name="to-implement-a-server-item"></a>K implementaci položka serveru

1. Odvodit třídu z `COleServerItem`.

1. Přepsání v odvozené třídě, `OnDraw` členskou funkci.

     Rámec volá `OnDraw` k vykreslení položky OLE do metasouboru. Aplikace typu kontejner používá tento metasoubor k vykreslení položky. Třídy zobrazení vaší aplikace má také `OnDraw` členskou funkci, která se použije k vykreslení položky, když je aktivní serverová aplikace.

1. Implementace přepsání `OnGetEmbeddedItem` pro třídu dokument na serveru. Další informace najdete v článku [servery: implementace dokumentů serveru](../mfc/servers-implementing-server-documents.md) ukázka MFC OLE a [HIERSVR](../visual-cpp-samples.md).

1. Implementace třídy položka serveru `OnGetExtent` členskou funkci. Rozhraní volá tuto funkci, aby se načetla velikost položky. Výchozí implementace nemá žádný účinek.

##  <a name="_core_a_tip_for_server.2d.item_architecture"></a> Tip pro architekturu položka serveru

Jak je uvedeno v [implementace položky serveru](#_core_implementing_server_items), serverových aplikací musí být schopna vykreslit položky v zobrazení serveru i v metasoubor používané aplikace typu kontejner. Do knihovny serveru Microsoft Foundation Class aplikace architektury, zobrazení tříd `OnDraw` členskou funkci vykreslí položky, když se upravuje (naleznete v tématu [CView::OnDraw](../mfc/reference/cview-class.md#ondraw) v *knihovny tříd* ). Položka serveru `OnDraw` vykresluje položky do metasouboru ve všech ostatních případech (viz [COleServerItem::OnDraw](../mfc/reference/coleserveritem-class.md#ondraw)).

Můžete se vyhnout duplikaci kódu zápis pomocné funkce ve třídě dokument na serveru a jejich z volání `OnDraw` funkce ve třídách zobrazení a položka serveru. Ukázky knihovny MFC OLE [HIERSVR](../visual-cpp-samples.md) používá tuto strategii: funkce `CServerView::OnDraw` a `CServerItem::OnDraw` obě volání `CServerDoc::DrawTree` vykreslit položku.

Zobrazení a položky mají `OnDraw` členské funkce, protože nakreslí v různých podmínkách. Zobrazení musí vzít v úvahu faktory, jako přiblížení, velikost výběru a rozsahu, výstřižek a prvky uživatelského rozhraní, jako jsou posuvníky. Položka serveru, na druhé straně vždy kreslení celý objekt OLE.

Další informace najdete v tématu [CView::OnDraw](../mfc/reference/cview-class.md#ondraw), [odvozenou třídu COleServerItem](../mfc/reference/coleserveritem-class.md), [COleServerItem::OnDraw](../mfc/reference/coleserveritem-class.md#ondraw), a [COleServerDoc::OnGetEmbeddedItem](../mfc/reference/coleserverdoc-class.md#ongetembeddeditem)v *tříd – referenční dokumentace ke knihovně*.

## <a name="see-also"></a>Viz také

[Servery](../mfc/servers.md)


---
title: 'Servery: Serverové položky | Microsoft Docs'
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
ms.openlocfilehash: e83b75183fe226b4ff384a00b0b5260caba01efa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="servers-server-items"></a>Servery: Serverové položky
Když kontejner spouští server tak, aby smí uživatel upravovat položky vložené nebo propojené OLE, je serverová aplikace vytvoří "položka serveru". Položka serveru, který je objektem třídy odvozené od `COleServerItem`, poskytuje rozhraní mezi dokumentu na serveru a aplikace kontejneru.  
  
 `COleServerItem` Třída definuje několik přepisovatelné členské funkce, které jsou volány OLE, obvykle v reakci na požadavky z kontejneru. Položky na serveru může představovat součástí serveru dokumentu nebo celý dokument. Když v dokumentu kontejneru vložené položky OLE, představuje položku serveru dokumentu celý server. Když je položka OLE připojena, položku serveru může představovat součástí serveru dokument nebo celý dokument, v závislosti na tom, jestli je odkaz na část nebo celý.  
  
 V [HIERSVR](../visual-cpp-samples.md) ukázkové, například třída položka na serveru, **CServerItem**, má člena, který je ukazatelem na objekt třídy **CServerNode**. **CServerNode** objektu je uzel v dokumentu HIERSVR aplikace, která je stromu. Když **CServerNode** objekt je kořenový uzel **CServerItem** objekt představuje celý dokument. Když **CServerNode** objekt je podřízený uzel, **CServerItem** objekt představuje část dokumentu. Viz ukázka MFC OLE [HIERSVR](../visual-cpp-samples.md) příklad této interakce.  
  
##  <a name="_core_implementing_server_items"></a> Implementace položky na serveru  
 Pokud použijete Průvodce aplikace k vytvoření "počáteční" kódu pro aplikace, všechny, které pokud chcete zahrnout položky na serveru do počáteční kód stačí je vyberte jednu z možností serveru na stránce možnosti OLE. Pokud přidáváte server položky do existující aplikace, proveďte následující kroky:  
  
#### <a name="to-implement-a-server-item"></a>K implementaci položku serveru  
  
1.  Odvození třídy z `COleServerItem`.  
  
2.  Přepsání v odvozené třídě, `OnDraw` – členská funkce.  
  
     Volání framework `OnDraw` k vykreslení položky OLE do metasoubory. Kontejner aplikace používá tento metafile k vykreslení položky. Třídy zobrazení vaší aplikace má také `OnDraw` členská funkce, které slouží k vykreslení položky, když je aktivní serverové aplikace.  
  
3.  Implementace přepsání `OnGetEmbeddedItem` pro váš server dokumentové třídy. Další informace najdete v článku [servery: implementace dokumentů serveru](../mfc/servers-implementing-server-documents.md) a ukázkové MFC OLE [HIERSVR](../visual-cpp-samples.md).  
  
4.  Implementace třídy položku serveru `OnGetExtent` – členská funkce. Volá rámec této funkci můžete načíst velikost položky. Výchozí implementace neprovede žádnou akci.  
  
##  <a name="_core_a_tip_for_server.2d.item_architecture"></a> Tip pro architekturu položka na serveru  
 Jak jsme uvedli v [implementace položky na serveru](#_core_implementing_server_items), serverové aplikace musí být schopna vykreslit položky v zobrazení serveru i v metasoubory používá aplikace kontejneru. V knihovny serveru Microsoft Foundation Class architektury aplikací, zobrazení třídy na `OnDraw` – členská funkce vykreslí položka, pokud je upravována (najdete v části [CView::OnDraw](../mfc/reference/cview-class.md#ondraw) v *knihovny tříd* ). Položku serveru `OnDraw` vykreslí položky do metafile ve všech ostatních případech (viz [COleServerItem::OnDraw](../mfc/reference/coleserveritem-class.md#ondraw)).  
  
 Duplikace kódu se můžete vyhnout tak, že zápis pomocných funkcí v třídě serveru dokumentu a volání je z `OnDraw` funkce ve vaší třídy zobrazení a položka na serveru. Ukázka MFC OLE [HIERSVR](../visual-cpp-samples.md) používá tato strategie: funkce **CServerView::OnDraw** a **CServerItem::OnDraw** obě volání **CServerDoc::DrawTree**  k vykreslení položky.  
  
 Zobrazení a položka mít `OnDraw` členské funkce, protože jejich kreslení v různých podmínkách. Zobrazení musí vzít v úvahu faktory, jako měřítka, výběr velikost a rozsah, výstřižek a prvky uživatelského rozhraní, jako jsou například posuvníky. Položku serveru, na druhé straně vždy nevykresluje celý objekt OLE.  
  
 Další informace najdete v tématu [CView::OnDraw](../mfc/reference/cview-class.md#ondraw), [COleServerItem](../mfc/reference/coleserveritem-class.md), [COleServerItem::OnDraw](../mfc/reference/coleserveritem-class.md#ondraw), a [COleServerDoc::OnGetEmbeddedItem](../mfc/reference/coleserverdoc-class.md#ongetembeddeditem)v *třídy referenční příručka knihovny*.  
  
## <a name="see-also"></a>Viz také  
 [Servery](../mfc/servers.md)


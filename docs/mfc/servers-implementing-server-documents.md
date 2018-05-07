---
title: 'Servery: Implementace dokumentů serveru | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE server applications [MFC], managing server documents
- OLE server applications [MFC], implementing OLE servers
- servers, server documents
- server documents [MFC], implementing
ms.assetid: cca1451a-ad09-47ed-b56e-bccd78fc86d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f15dbd16b48aade59470bfbf7e84faf4aeb03c61
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="servers-implementing-server-documents"></a>Servery: Implementace dokumentů serveru
Tento článek vysvětluje kroky, které je nutné provést při úspěšně implementovat dokument na serveru, pokud jste nezadali možnost OLE serveru v Průvodci aplikací.  
  
#### <a name="to-define-a-server-document-class"></a>Chcete-li definovat dokumentové třídy serveru  
  
1.  Odvození třídě dokumentu z `COleServerDoc` místo **CDocument**.  
  
2.  Vytvoření položky serveru třídy odvozené od `COleServerItem`.  
  
3.  Implementace `OnGetEmbeddedItem` funkce člena třídy dokumentů serveru.  
  
     `OnGetEmbeddedItem` je volána, když uživatel aplikace kontejner vytvoří nebo upraví vložené položky. Měla by vrátit položku představující celý dokument. To by měla být objekt vaší `COleServerItem`-odvozené třídy.  
  
4.  Přepsání `Serialize` – členská funkce určená k serializaci obsah dokumentu. Není nutné k serializaci seznamu položky na serveru, pokud je používáte představující nativní data v dokumentu. Další informace najdete v tématu *implementace položky na serveru* v článku [servery: Server položky](../mfc/servers-server-items.md).  
  
 Když je vytvořen dokument na serveru, rozhraní automaticky zaregistruje dokumentu se OLE systémové knihovny DLL. To umožňuje knihovny DLL pro identifikaci dokumenty na serveru.  
  
 Další informace najdete v tématu [COleServerItem](../mfc/reference/coleserveritem-class.md) a [COleServerDoc](../mfc/reference/coleserverdoc-class.md) v *knihovny tříd*.  
  
## <a name="see-also"></a>Viz také  
 [Servery](../mfc/servers.md)   
 [Servery: Serverové položky](../mfc/servers-server-items.md)   
 [Servery: Implementace serveru](../mfc/servers-implementing-a-server.md)   
 [Servery: Implementace oken s rámečkem na místě](../mfc/servers-implementing-in-place-frame-windows.md)

